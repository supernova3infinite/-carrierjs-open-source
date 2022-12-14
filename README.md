# -carrierjs-open-source
Carrier JS is promise based http client for browsers. It is used to interact with servers with ultimate caching feature. 

Carrier helps you implement new-line terminated protocols over node.js.

The client can send you chunks of lines and carrier will only notify you on each completed line.
Install

$ npm install carrier

Usage

var net     = require('net'),
    carrier = require('carrier');
 
var server = net.createServer(function(conn) {
  carrier.carry(conn, function(line) {
    console.log('got one line: ' + line);
  });
});
server.listen(4001);

Or, you can also listen to the "line" event on the returned object of carrier.carry() like this:

var net     = require('net'),
    carrier = require('carrier');
 
var server = net.createServer(function(conn) {
  var my_carrier = carrier.carry(conn);
  my_carrier.on('line',  function(line) {
    console.log('got one line: ' + line);
  });
});
server.listen(4001);

carrier.carry accepts the following options:

  carrier.carry(reader, listener, encoding, separator)

    reader: the stream reader
    listener: a "line" event listener function
    encoding: what encoding to assume. Default: "utf8"
    separator: what line separator to use. Default: /\r?\n/

All are optional except for the first.

