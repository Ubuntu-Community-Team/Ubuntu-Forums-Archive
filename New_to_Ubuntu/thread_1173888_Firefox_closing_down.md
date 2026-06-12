---
title: "Firefox closing down"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by clive littlewood on 2009-05-30
Hi Folks

Have been running jaunty from release and have had no problems with Firefox.

Then today Firefox will start and load the home page then close it'self.

I have started Firefox in a terminal and get this error message

```
The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 5048 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```


Any thoughts would be appreciated.

Thanks

Clive

---

### Post by cmnorton on 2009-05-31
At least someone knows about the problem:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/231719](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/231719)

You might consider adding your information to this bug, unless the original submitter covered your problem exactly.

---

### Post by clive littlewood on 2009-05-31
Hi cmnorton

Thanks for your interest I have added to the bug report.

I have also tried lots of different things to no avail.

I did a re-install today and upto now have not had a repeat of the problem.

Regards

Clive

---

