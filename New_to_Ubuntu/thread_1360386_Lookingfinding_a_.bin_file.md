---
title: "Looking/finding a .bin file"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by suomalainen on 2009-12-20
Ubunteros,

I have a Lite-on burner and the latest firmware file can be found on Liteon's website via:

[http://us.liteonit.com/us/index.php?option=com_wrapper&Itemid=153](http://us.liteonit.com/us/index.php?option=com_wrapper&Itemid=153)

I thought that if I downloaded this file I could "right" click on it and use "Archive Manager" to see the .bin file. but this did not work.

Who wouldn't mind teaching me what it is that I need to do to find the .bin file????

Thanks and Merry Christmas.....

---

### Post by lemming465 on 2009-12-24
I'm assuming that you found the file OK, probably in ~/Downloads, unless you saved it elsewhere.  (If not, at a command prompt run *find ~ -name "*.bin" -print* and it will probably turn up.)

If the GUI archive manager doesn't understand it, at a command prompt run "file ..." against it and see if it can be identified.  One possibility is that the firmware is just an opaque binary blob of stuff which some other program is intended to upload to the drive.  Unfortunately the other program often is windows-only.

Another possibly useful command to run against it is "strings", which will try to list any printable character sequences (version, error messages, ...) which happen to appear in it.

Worst case scenario, you can scrutinize it with a hex dump utility such as "xxd" and get some insight.

---

