---
title: "Anti virus for 9.10"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by gooliwoop on 2010-02-21
I got a LINUX The Complete Manual with a copy of Ubuntu 9.10 which tells me I should download a free copy of anti-virus from [http://tinyurl.com/dymsjb](http://tinyurl.com/dymsjb) after having obtained a key from [http://tinyurl.com/ydun6v](http://tinyurl.com/ydun6v). I've got the key and downloaded 2 versions of the software; one for a 32 bit machine and one for a 64 bit machine (I don't know what my old laptop is). I am then instructed to type the following command into Terminal but when I do it's not recognised:
cd /Desktop
I am then instructed to type:
sudo sh Bit 
and press tab and enter the key. I haven't got this far yet.

I have read other threads telling me that AV is not necessary with Linux but I'm not convinced and seeing that the software is free I can't see that it would do any harm. 

can anyone tell me why the command cd /Desktop doesn't work and how I can fix it please?

---

### Post by nos09 on 2010-02-21
> **gooliwoop said:**
> I got a LINUX The Complete Manual with a copy of Ubuntu 9.10 which tells me I should download a free copy of anti-virus from [http://tinyurl.com/dymsjb](http://tinyurl.com/dymsjb) after having obtained a key from [http://tinyurl.com/ydun6v](http://tinyurl.com/ydun6v). I've got the key and downloaded 2 versions of the software; one for a 32 bit machine and one for a 64 bit machine (I don't know what my old laptop is). I am then instructed to type the following command into Terminal but when I do it's not recognised:
cd /Desktop
I am then instructed to type:
sudo sh Bit 
and press tab and enter the key. I haven't got this far yet.

I have read other threads telling me that AV is not necessary with Linux but I'm not convinced and seeing that the software is free I can't see that it would do any harm. 

can anyone tell me why the command cd /Desktop doesn't work and how I can fix it please?

> codename-nos@codename-nos-desktop:~$ 

if you can see something like this then 
i guess you are already on desktop

---

### Post by spongypants23 on 2010-02-21
> **gooliwoop said:**
> I got a LINUX The Complete Manual with a copy of Ubuntu 9.10 which tells me I should download a free copy of anti-virus from [http://tinyurl.com/dymsjb](http://tinyurl.com/dymsjb) after having obtained a key from [http://tinyurl.com/ydun6v](http://tinyurl.com/ydun6v). I've got the key and downloaded 2 versions of the software; one for a 32 bit machine and one for a 64 bit machine (I don't know what my old laptop is). I am then instructed to type the following command into Terminal but when I do it's not recognised:
cd /Desktop
I am then instructed to type:
sudo sh Bit 
and press tab and enter the key. I haven't got this far yet.

I have read other threads telling me that AV is not necessary with Linux but I'm not convinced and seeing that the software is free I can't see that it would do any harm. 

can anyone tell me why the command cd /Desktop doesn't work and how I can fix it please?

There is no folder at /Desktop

Try Just "cd Desktop", without the slash before the D.

---

### Post by nos09 on 2010-02-21
Anti virus is important and its free. ( i dont use it by myself )and i m actually very neutral about this.

but you can find this one helpful [http://www.n00bsonubuntu.com/software/clamav]("http://www.n00bsonubuntu.com/software/clamav")

---

### Post by spiky001 on 2010-02-21
The threads are right anti virrus is not nessecary, as for software all the software is free, if you wanted there is an easier way to get it via synaptic manager will install it all for,might be easie as you are new to OS

---

### Post by Sef on 2010-02-21
>  I have read other threads telling me that AV is not necessary with Linux  but I'm not convinced and seeing that the software is free I can't see  that it would do any harm. 

1) There are no viruses currently for Linux.   The only time one would need an anti-virus would be if one ran an email client, so one does not infect their friends computer.

2) Be sure and capitalize the D in desktop.

---

### Post by PenguinInside on 2010-02-21
You don't need an antivirus for Linux. If you want to run one anyways, use the clamav package, which is a supported Ubuntu package that you can install easily from the repositories:

```
sudo apt-get install clamav
```

---

### Post by eriktheblu on 2010-02-21
Firefox in Karmic (9.10) by default downloads to your Downloads (or Download maybe, ls ~ to make sure) directory rather than your desktop. That may present an issue later on.

Instead of cd /Desktop try ```
cd ~/Desktop
```This will put you in your user desktop directory. If your download is located there, continue as instructed.

If your download is instead in your Downloads directory, use ```
cd ~/Downloads
```

As others have mentioned, easier still to grab Clam from the software center.

---

### Post by dream_coder on 2010-02-21
easier to just type cd ~/Desktop

---

### Post by ikt on 2010-02-21
> **Sef said:**
> 1) There are no viruses currently for Linux.   The only time one would need an anti-virus would be if one ran an email client, so one does not infect their friends computer.

2) Be sure and capitalize the D in desktop.

No viruses, what about malware?

---

### Post by Girya on 2010-02-21
The last active security threat for Linux that I could find was Aug 2008, it wasn't a virus it was a SSH based attack. The fix seems to have been  released two days before the threat was reported. Here's the link:

[http://www.us-cert.gov/current/archive/2008/08/27/archive.html#ssh_key_based_attacks]("http://www.us-cert.gov/current/archive/2008/08/27/archive.html#ssh_key_based_attacks")

I think I am much more vulnerable to attacks where someone tricks me into typing malicious code at the terminal. I feel I'm much better protected by trying to learn as much as possible about the o/s and it processes

---

### Post by PenguinInside on 2010-02-21
By the way, do you have a hardware-based firewall (such as one of the cheap Netgear WGR640 routers)? If so, you're already much of the way there as far as security goes.

As far as anti-viruses go, BitDefender (which you linked to) is pretty good, though. I [used it]("http://www.digitivity.org/329/removing-conficker-and-sasser-viruses-from-windows-xp-with-kaspersky-and-bitdefender-rescue-cd-linux-ubcd") when cleaning up my Windows XP before moving to Ubuntu.

Regarding malicious code, I think you should have a separate user account in which you do tinkering. If you're still learning, don't have a lot of important files in the same account that you're using for entering unknown commands.

And don't install random software, stick to the Ubuntu Software Center.

To be on the safe side, don't run any command beginning with "sudo" until you've double-checked it on the [Ubuntu wiki]("https://wiki.ubuntu.com/").

---

### Post by kid1000002000 on 2010-02-21
Antivirus software is not necessary, though possible.  Likely you may end up finding a file or two that is dormant on a linux environment but could have disabled a windows machine.  Nothing to worry about!   with the few av programs out there, future attacks will probably just be fixed by a linux update, etc.

---

### Post by Paul T. on 2010-02-22
> **Girya said:**
> The last active security threat for Linux that I could find was Aug 2008, it wasn't a virus it was a SSH based attack. The fix seems to have been  released two days before the threat was reported. Here's the link:

[http://www.us-cert.gov/current/archive/2008/08/27/archive.html#ssh_key_based_attacks]("http://www.us-cert.gov/current/archive/2008/08/27/archive.html#ssh_key_based_attacks")

I think I am much more vulnerable to attacks where someone tricks me into typing malicious code at the terminal. I feel I'm much better protected by trying to learn as much as possible about the o/s and it processes


There was a malware threat to Linux in December last year:

[http://en.wikipedia.org/wiki/Linux_malware#Viruses_and_trojan_horses](http://en.wikipedia.org/wiki/Linux_malware#Viruses_and_trojan_horses)

---

### Post by nos09 on 2010-02-24
> **Paul T. said:**
> There was a malware threat to Linux in December last year:

[http://en.wikipedia.org/wiki/Linux_malware#Viruses_and_trojan_horses](http://en.wikipedia.org/wiki/Linux_malware#Viruses_and_trojan_horses)

did you remember the famous "New folder" virus of windows ? in which the virus will create an additional folder in your HD or usb according to your folder on the drive.
4 months ago i got it on ubuntu. its hard to believe but true.
like in music folder-- music.exe , in picture-- picture.exe and so on almost every folder got the named exe file. i was able to delete it but it came back each time i reboot.. funny !!!!

but the best part is it didn't effect my system. it was not able to create system load on linux !!! hahahah gottcaha 

anyother had these kind of problems in linux ?

---

