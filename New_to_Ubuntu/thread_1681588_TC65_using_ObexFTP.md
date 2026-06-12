---
title: "TC65 using ObexFTP"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by insectatorious on 2011-02-04
Hi,
   I apologise if this has been posted elsewhere but I have searched carefully without any luck so far. My problem is as follows:

I have a [TC65 Modem]("http://www.cinterion.com/tc65t.html").

The modem is connected to my desktop via a USB-Serial converter (as my desktop doesn't have a serial port). Using GtkTerm I can run 'at' commands on the modem. I cannot however, access the files that are on the modem or even add new ones.

I am following the instructions [laid out here]("http://www.xargs.com/linux/tc65-linux.html"). 

The specific portion is:

[I]The necessary changes to ObexFTP are:
[LIST]
[*]Change the baud rate in bfb_io.c:bfb_io_open() to 115200
[*]Also in bfb_io.c:bfb_io_open(), add a "goto newsiemens;" after the response to the ATZ command has been read. ObexFTP already supports the necessary command to put the TC65 into OBEX mode, but its attempt to probe for other phone and protocol types causes the two to get out of sync.
[*]Just prior to closing the file descriptor in bfb_io.c:bfb_io_close(), add a call to write() to send a +++ string to exit OBEX mode. There should be a one-second guard time (sleep (1); ) prior to sending the +++.
[/LIST]
[/I]

**Where can I find this file: *bfb_io*?**

Is there an alternative means of accessing the files on the modem?

Thanks.

---

### Post by 3esmit on 2011-02-07
Hello insectatorious

What do you need to do in TC65 ? Transfer files or use it as a modem?

An already hacked obexftp sources by me (following this guide) is available here [http://groups.google.com/group/javacint/files](http://groups.google.com/group/javacint/files) (obexftp-0.23.tar.bz2) 
newer versions from obexftp will not work with this guide, becouse the UUID from connection is not compatible with TC65.

Also for transfer files you can use my JObexFTP solution available here [http://www.github.com/3esmit/JObexFTP](http://www.github.com/3esmit/JObexFTP)

---

