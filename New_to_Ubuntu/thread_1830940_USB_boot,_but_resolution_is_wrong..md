---
title: "USB boot, but resolution is wrong."
date: 2011-08-22
forum: New to Ubuntu
---

### Post by johncmolyneux on 2011-08-22
Hi guys, 

After many years using Windows, I've finally decided to have a go with Linux. I downloaded Ubuntu 11.04 and, following the instructions on the download page, installed it onto a USB drive. 

Everything boots fine, but after the initial menu I get a purple screen that is corrupted in the manner that I'm familiar with from setting Windows to run at an unsupported resolution. 

At the boot menu I've found that pressing escape allows me to enter boot options. By doing this I have been able to try many different resolutions, but they all show the same results. 

Obviously, I can't actually do anything within Ubuntu itself as I can't see anything, so does anyone have any suggestions? 

Thanks in advance.

---

### Post by johncmolyneux on 2011-08-23
Can anyone help with this please?

---

### Post by johncmolyneux on 2011-08-23
If I've not given enough info then please let me know what you need.  If I've not explained the problem well enough then please let me know.

---

### Post by realzippy on 2011-08-23
which boot options have you tried already?

---

### Post by johncmolyneux on 2011-08-23
> **realzippy said:**
> which boot options have you tried already?

When I press escape I get the prompt "Boot:".  I read up about  different resolutions on a wiki page and tried vga=987.  This wasn't a supported value, so I was presented with a list of possible options.  I've been through every single one of them with no joy.  It's exactly the same, regardless of what I do.

---

### Post by realzippy on 2011-08-23
So you tried also vga=771 ?

If so,try "nomodeset"  (without quotes)

---

### Post by johncmolyneux on 2011-08-23
Yes, I've tried both of those and had the exact same issue.

Just to be clear, the boot menu that I am getting to is where I have the option to install Ubuntu to my PC or to boot from the USB HD.  Is the "Boot:" prompt meant to take command-line parameters?

---

### Post by johncmolyneux on 2011-08-23
Straight after the aforementioned purple screen, and get this...

---

### Post by johncmolyneux on 2011-08-24
Am I asking in the wrong forum or something?

---

### Post by realzippy on 2011-08-24
No,
but thread title is misleading.
It looks like as you don't get a usable screen at all.
You have a CDrom?
Does a liveCD boot to desktop GUI ?

---

### Post by johncmolyneux on 2011-08-24
Thanks for the reply.

I've not made a CD.  I followed the instructions on this page...

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

but they look exactly the same for CD or USB.  Would running from a CD make a difference?

Also, if the thread's badly titled, how would you suggest I title it?  Over 130 views but you're the only one that's offered any thoughts so far.

---

### Post by realzippy on 2011-08-24
I would suggest to try a live CD before thinking about a new thread/title.
Yes,I have seen people running into the problem that the live CD booted
fine to desktop GUI,but booting the install failed.
Please check this out if it is no problem for you downloading an CD ISO
due to limited bandwidth.

---

