---
title: "Failed to start x server on new install"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Gmagn on 2009-02-22
Hello,

I'm trying to renew an old computer.

I'm very new to this and followed prompts to view the x server output:

debconf: DbDriver "connfig": /var/cache/debconf/config.dat is locked by another process: Resource temporily unavailable Warning: Could not generate /etc/x11/xorg.config.failsafe for vesa driver.

I'm trying this on an old AMD-K6 3D processor, 367 MHz, 252 MB RAM, 7.83GB used, 1.69 GB free.

I am stalled on a command line prompt

ubuntu@ubuntu:~$

Any ideas to get Ubuntu running on this computer?

---

### Post by stalkier on 2009-02-22
> **Gmagn said:**
> Hello,

I'm trying to renew an old computer.

I'm very new to this and followed prompts to view the x server output:

debconf: DbDriver "connfig": /var/cache/debconf/config.dat is locked by another process: Resource temporily unavailable Warning: Could not generate /etc/x11/xorg.config.failsafe for vesa driver.

I'm trying this on an old AMD-K6 3D processor, 367 MHz, 252 MB RAM, 7.83GB used, 1.69 GB free.

I am stalled on a command line prompt

ubuntu@ubuntu:~$

Any ideas to get Ubuntu running on this computer?

I could be wrong here, but I think the command would be 'startx'.
Like I said I might be wrong. There is also a way to force the vesa driver. I do not know how to do that at the moment though. Sorry.

---

### Post by Gmagn on 2009-02-22
Thanks for your quick reply.

I tried startx and got this:

Fatal server error:
no screens found
giving up.
xinit: Connection refused (errno 111): unable to connect to x server 

ubuntu@ubuntu:~$

---

### Post by superprash2003 on 2009-02-22
i hope this helps [http://www.prash-babu.com/2008/11/how-to-fix-no-screen-found-error-in.html](http://www.prash-babu.com/2008/11/how-to-fix-no-screen-found-error-in.html)

---

### Post by Gmagn on 2009-02-22
Thank you superprash2003.  I followed the instructions and got this:

(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screen found
giving up.
xinit: Connection refused (errno 111): unable to connect to x server
xnit: No such process (errno 3): Server error.
ubuntu@ubuntu:~$ _

---

### Post by Gmagn on 2009-02-22
Any other ideas?  Anyone else find a solution to this problem?

---

### Post by superprash2003 on 2009-02-25
reconfiguring the package as shown in the tutorial didnt help?

---

### Post by Gmagn on 2009-02-25
superprash2003,

I went through all of the instructions and got:

(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screen found
giving up.
xinit: Connection refused (errno 111): unable to connect to x server
xnit: No such process (errno 3): Server error.
ubuntu@ubuntu:~$ _ 

Any other ideas?  I had an easy install on my laptop and think Ubuntu is great. I would love to resurrect this old computer rather than throwing it out ...

---

### Post by chris200x9 on 2009-02-25
maybe try ```
X -configure
``` then follow the on screen prompts

---

### Post by Gmagn on 2009-02-25
Thanks, chris200x9,

I tried your suggestion and got back this:

The '-configure' option can only be used by root.

Don't quite know where to go from here?

---

### Post by chris200x9 on 2009-02-25
hmmm bear with me for a moment (I don't use ubuntu) maybe try ```
 sudo X -configure
``` and input your password.

---

### Post by Gmagn on 2009-02-25
Well, I tried that and am still back at the command prompt.  Here's the last couple of lines:

Your xorg.conf file is /home/ubuntu/xorg/conf.new

To test the server, run 'X -config /home/ubuntu/xorg.conf.new

I tried that and got this:

Fatal server error:
no screens found
ubuntu@ubuntu:~$

---

### Post by chris200x9 on 2009-02-25
this may be a dumb question but, do you have a video card installed? If so are you sure it's working properly?

---

### Post by Gmagn on 2009-02-26
I don't know about a video card as I mentioned it's an old computer.  I can tell you that when I run the Ubuntu live CD, the Ubuntu logo is properly displayed and the progress bar also shows properly.  It is only at the end of the installation process that the screen switches to a black and while command line prompt.  If you think this is a video card problem can you point me in a direction to troubleshoot that, or even how to find out if this old computer has a proper video card to run Ubuntu?

Thanks.

---

### Post by chris200x9 on 2009-02-26
try an 'lspci' to see if you have a video card if you don't you may have to pick one up cheap

---

### Post by wlraider70 on 2009-02-26
This might not help but...

When i first installed ubuntu, i got the server version, because i wanted to make a server and it out mu into the command line.

the command line was way too advanced for me.

did u install the desktop version, and how about reinstalling could there have been an error in the gnome install.

---

### Post by Gmagn on 2009-02-26
Thanks for staying with me on this ...

I tried the lspci and got several messages, the one I think is related is this:

00:1133.0 VGA compatible controller: Silicon Integrated Systems [SiS] 5597/5598/63 26 VGA (rev 68)

Does this identify the video card?

---

### Post by Gmagn on 2009-02-26
wlraider70,

I'm trying to install the desktop version.  The command line prompts are way over my head too.  It goes through the install showing the Ubuntu logo and the progress bar, then, the screen goes blank and then opens up to just the black screen with white characters and the command line interface.

---

### Post by wlraider70 on 2009-02-26
did u ever run from a live CD?
when you dont install the OS?

Do you get any GUI (graphical user interface) that way.

---

### Post by Gmagn on 2009-02-26
Yes, I did try to install from Live CD just to try and it did the same thing.

---

