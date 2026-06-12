---
title: "VIM + Xdebug = Error Code 5"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by thale on 2009-02-19
Hey guys,

I'm a PHP developer and I've started using vim recently. I can get around pretty quick but I'm not a total pro yet.

My issue is I followed this tutorial: [http://www.apaddedcell.com/easy-php-debugging-ubuntu-using-xdebug-and-vim](http://www.apaddedcell.com/easy-php-debugging-ubuntu-using-xdebug-and-vim)

for hooking xdebug up to vim for debugging local php. It seemed to work with out a hitch until I actually try and step through or run to a break point then I receive this error and it drops the connection:
```
response xmlns:xdebug=http://xdebug.org/dbgp/xdebug xmlns=urn:debugger_protocol_v1 command=stack_get transaction_id=6
error code=5 : Command not available (Is used for async commands. For instance if the engine is in state "run" than only "break
message
command is not available
```

It seems like there is a possible version miss match or I possibly missed something when I set it up. Any insight would be appreciated.

---

### Post by blueridgedog on 2009-02-22
I suggest you post your issue to the xdebug mailing list:

[http://www.xdebug.org/support.php](http://www.xdebug.org/support.php)

I bet you will get some help there.  Good luck.

---

### Post by simoncoggins on 2009-11-08
I had the same problem using xdebug + vim on ubuntu. The problem (for me) was that I was setting breakpoints on blank lines - make sure you put the breakpoint on a line with valid code!
 

See also this thread:
[http://xdebug.org/archives/xdebug-general/1202.html](http://xdebug.org/archives/xdebug-general/1202.html)


Simon

---

