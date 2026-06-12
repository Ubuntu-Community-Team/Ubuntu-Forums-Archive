---
title: "Ubuntu 10.04/11.04, print on Lexmark X2670"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by mkornig on 2011-05-24
Hi there,

I got a new computer and a new printer last week. The supplier said the printer is very Linux compatible...

Automatic printer/driver installation doesn't work. I've studied the online Ubuntu documentation. I've tried many things. Still I can't print.


[LIST=1]
[*]Can anybody help? I would probably need guidance through the whole driver installation process for a certain time. Or a detailed, easy to understand documentation?
[*]Is there a better place in the forum to post a question like this and to get help?
[*]Has anybody ever succeeded in printing on this printer under Ubuntu 11.04?
[*]Would I face the same problems under an older version, say Ubuntu 10.04?
[/LIST]

---

### Post by compmodder26 on 2011-05-24
Here is a thread that details the installation of the driver:

[http://ubuntuforums.org/showthread.php?p=8652097](http://ubuntuforums.org/showthread.php?p=8652097)

---

### Post by compmodder26 on 2011-05-24
In case those instructions are hard to follow:

1.  Go here: [http://support.lexmark.com/index?page=productSelection&locale=EN&userlocale=EN_US](http://support.lexmark.com/index?page=productSelection&locale=EN&userlocale=EN_US)

2.  You should see a search box.  In that box type x2670.  As you are typing, it should narrow your search to your printer model.  Under the picture of your printer, click "Select".

3.  On the page that appears, you should see a tab called "Downloads" at the bottom of the page.  In that tab you'll see "See Downloads for Linux/Unix >>"

4.  Click that and it will expand with options.  Click the one that says "Printer Driver for Debian Package Manager based distros".

5.  You'll see a popup that has a button at the very bottom to download the file.

6.  On that same popup window are instructions for installing.


Hope this helps!

---

### Post by compmodder26 on 2011-05-24
Thought I would try a test installation and one thing you'll want to change is in the instructions that you follow on the lexmark site, you'll need to do option "A" and step 3 where it says:

Use the following command to install the driver 
```
./lexmark-inkjet-[xx]-driver-[x.x.x]..i386.deb.sh
```

You instead need to do:

```
sudo ./lexmark-inkjet-[xx]-driver-[x.x.x]..i386.deb.sh
```

---

### Post by mkornig on 2011-05-24
Thanks a lot cmpmodder26!

I've downloaded a driver from the Lexmark site for my printer. It's called:
[INDENT]*lexmark-inkjet-08-driver-1.0-1.i386.deb.sh*
[/INDENT]I'm not sure whether this driver is suitable for my system.

But I tried it nevertheless. When I execute it (as super user) I get an error 
message saying:
[INDENT]*Warning: No installer for "x86_64" found, defaulting to x86...*
[/INDENT]and finally:
[INDENT]*Error: Couldn't find any suitable frontend for your system*
[/INDENT]I'll attach the dump in a text file.

Now: what can I do about this missing frontend/installer? Is it wothwhile digging any further?

Help, please!

---

### Post by compmodder26 on 2011-05-24
Looks like the driver doesn't support 64 bit architectures.  And this thread appears to confirm that:

[http://ubuntuforums.org/showthread.php?t=1498529](http://ubuntuforums.org/showthread.php?t=1498529)

Not sure what to tell you now. :(

---

### Post by mkornig on 2011-05-24
I tried the following:

[LIST=1]
[*]I installed the installer *gdebi *
[*]Then I tried to execute the above mentioned sh-file again.
[*]Unfortunately I got exactly the same error messages.
[/LIST]

---

### Post by fritz269 on 2011-05-24
I have a Lexmark X6650 and I guess I am going to have the same issue since it only has the 32-bit drivers for it.

---

### Post by mkornig on 2011-05-24
Here is a thought:

There are Ubuntu versions for 32 and 64bit architectures. Right?
Could I install a 32bit Ubuntu on my computer? And would it work? Just as fine?
Then I might be able to make use of my printer. Right?

Or is this complete nonsense?

---

### Post by compmodder26 on 2011-05-24
You should be able to install the 32 bit Ubuntu just fine.

---

### Post by fritz269 on 2011-05-25
I was able to install the driver for my x6650.
 Try this code below. It worked for me but i replaced it with your driver.  First make sure you are in the correct folder the type

```
sudo sh /*lexmark-inkjet-08-driver-1.0-1.i386.deb.sh*
```

if that does not work remove the first slash

---

### Post by mkornig on 2011-05-25
I installed Ubuntu 10.04 32bit. And the with a little struggle about the *root password,* see [http://ubuntuforums.org/showthread.php?t=1767508](http://ubuntuforums.org/showthread.php?t=1767508) for reference, I was able to install the Lexmark printer.

It prints alright now.

By the way: 10.04 seems to work better for me than 11.04, in many respects...

Thanks for your support, everybody. Once again I'm impressed by the efficiency of this forum.

---

### Post by FrF on 2011-05-28
> **mkornig said:**
> I installed Ubuntu 10.04 32bit. And the with a little struggle about the *root password,* see [http://ubuntuforums.org/showthread.php?t=1767508](http://ubuntuforums.org/showthread.php?t=1767508) for reference, I was able to install the Lexmark printer.

It prints alright now.

By the way: 10.04 seems to work better for me than 11.04, in many respects...


Very interesting, mkornig! How about scanning with the X2670? Does it work, too? I'm still running Hardy (Ubuntu 8.04) just because I want to keep the X2670's full functionality :-) To recap: The Debian-based driver from Lexmark doesn't just work with 8.04 but at least also with 10.4? I wondered about this because the current Debian driver is, according to Lexmark, an update from May 2011 and it would be a bit strange if they didn't support the other recent LTS release.

Take care!
FrF

---

### Post by mkornig on 2011-05-29
To FrF:

I haven't tested scanning yet. I'll try today and report back.

Yes, printing under Ubuntu 10.04 LTS **32 bit** works fine for me with Lexmark's driver. But I was **not** able to print under 11.04 **64 bit**. I haven't chekced the 32 bit version of 11.04.

---

### Post by mkornig on 2011-05-29
*Simple Scan* works, too. It's straight forward and easy to use. Actually, the resolution is stunning!

---

### Post by FrF on 2011-05-29
> **mkornig said:**
> *Simple Scan* works, too. It's straight forward and easy to use. Actually, the resolution is stunning!

Thanks, mkornig! Lucid Lynx, here I come :-)

---

