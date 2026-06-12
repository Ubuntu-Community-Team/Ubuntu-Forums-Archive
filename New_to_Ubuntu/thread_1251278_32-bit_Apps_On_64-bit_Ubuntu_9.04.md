---
title: "32-bit Apps On 64-bit Ubuntu 9.04?"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by carl_76 on 2009-08-27
Hi.

I have a 32-bit engineering application that I would like to install.  I am running 9.04 on an amd64 laptop.  Is there a method that would alowl my system to run any 32-bit application?

Thanks.

Carl

---

### Post by NoaHall on 2009-08-27
dpkg -i --force-architecture or compile it yourself

---

### Post by Tibuda on 2009-08-27
Yes, you may need to install some 32bit libraries tough. Search for the ia32-libs packages in Synaptic.

---

### Post by carl_76 on 2009-08-27
I this case the setup script is called xsetup so I should type: 

dpkg -i --force-architecture xsetup

correct? Linux commands are completely new to me.

Thanks.

---

### Post by NoaHall on 2009-08-27
No, you need to put the location +name of the file you wish to force at the end  and run it in the terminal ( Applications -> Accessories -> terminal)
For example:
dpkg -i --force-architecture /home/noah/Desktop/package.deb

---

### Post by jerome1232 on 2009-08-27
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Getlibs helps if you need some 32 bit libraries to run it. Other than that running a 32 bit app isn't any different.

---

### Post by carl_76 on 2009-08-28
Hi.

I tried running the installation script with the terminal command in this format:

dpkg -i --force-architecture /home/noah/Desktop/package.deb

However, I got an error because the script is not a .deb file.

So, maybe I've been asking the wrong question...  Since the installer is an executable program in itself, is there a way to run it in a 32bit mode/shell, etc?

I found, on a separate forum, a user who was running this program - once installed - on a amd64 machine simply by editing a setup file that told the program it was on a 32bit machine.

Thanks for the help.

Carl

---

### Post by Perfect Storm on 2009-08-28
If it's a binary
```
cd ~/Desktop
ldd <name-of-the-binary-file>
```
Then we can see what you're missing.


Or try;
```
chmod +x <execute-file>
./<execute-file>
```


Anyway, what are you trying to use?

---

### Post by carl_76 on 2009-08-28
Hi.

I will give those commands a try and let you know what I find, tomorrow.  It's pretty late in this time zone.  

I'm trying to use Xilinx ISE WebPack 11.1.  It's the only free version of the tool they have.  I haven't used ISE in a few years and I wanted to get familiar with it again for upcoming job interviews.

I may have stumbled across another forum, just now, that tells me what I have to do to install it, message 5 of 8:  [http://forums.xilinx.com/xlnx/board/message?board.id=INSTALLBD&message.id=156&query.id=741196#M156](http://forums.xilinx.com/xlnx/board/message?board.id=INSTALLBD&message.id=156&query.id=741196#M156)

I've been looking for this for a while now.  Again, I'll try that tomorrow also and report back.

Thanks for all the help.  This is my first time using linux and so far I'm feeling good about it.  The support has been great.

Carl

---

### Post by carl_76 on 2009-09-11
Hi.

I installed WebPack 11.2i on my laptop and am able to run ISE. I have not run any of the other applications. I am running 9.04 64-bit on a dual core amd64 laptop. I had to install out of the /bin/lin directory per Xilinx instructions since WebPack is a 32-bit application. The updater worked fine after the initial install.

---

