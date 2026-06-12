---
title: "How do I play an MP3 file in Ubuntu?"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by Rabz on 2009-07-10
i cant get this OS figured out :(

---

### Post by nothingspecial on 2009-07-10
What`s the problem(s)?

---

### Post by credobyte on 2009-07-10
Can you be more specific ?

---

### Post by philinux on 2009-07-10
> **Rabz said:**
> i cant get this OS figured out :(

Wait a minute I'll get my crystal ball out. :lolflag:

---

### Post by TheGreenFox on 2009-07-10
Welcome to the forums,

If your having a problem just describe it to your best knowledge and we will all do our best to help you.

*Christopher Sleys*

---

### Post by halitech on 2009-07-10
without knowing what issues you are having its going to be hard to help out but first thing to do is forget whatever you know about windows and stop trying to apply it to Ubuntu. Linux is not windows and windows is not linux. They both do things differently so if you try and keep a windows user mindset, you will get frustrated fast.

---

### Post by scorp123 on 2009-07-10
> **halitech said:**
> without knowing what issues you are having its going to be hard to help out but first thing to do is forget whatever you know about windows and stop trying to apply it to Ubuntu. Linux is not windows and windows is not linux. They both do things differently so if you try and keep a windows user mindset, you will get frustrated fast.

+1 & "amen!" to that.

And here the link:

"Linux is NOT Windows!"
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Rabz on 2009-07-10
thank you.. im a technician on windows.. that could be the problem :$

im really just trying to start with the basics. i went through the manuals..

i would like to play a song (mp3 format).. then it has to search for a suitable plugin.. then it tells me that no packages with the requested plugins could be found.. then i get an error message saying: "the playback of this movie requires a MPEG-1 Layer 3 (MP3) decoder plugin which is not installed.

so im guessing that the next step would be installing/updating packages??

---

### Post by credobyte on 2009-07-10
```
sudo apt-get install ubuntu-restricted-extras

```

This command will solve a lot of your problems ( mp3, flash, rar files, etc. ) ;)

---

### Post by CatKiller on 2009-07-10
> **Rabz said:**
> i would like to play a song (mp3 format)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by philinux on 2009-07-10
Also click the medibuntu link below.

---

### Post by Rabz on 2009-07-10
> **credobyte said:**
> ```
sudo apt-get install ubuntu-restricted-extras

```This command will solve a lot of your problems ( mp3, flash, rar files, etc. ) ;)

then i get the following return:

rabz@A3:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for rabz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

---

### Post by nothingspecial on 2009-07-10
[[COLOR="Magenta"]This[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683") will solve all the issues that the ubuntu restricted extras package resolves and more.


I`ve been told it`s not learning linux that is difficult - rather it`s unlearning windows.

---

### Post by whole.grains on 2009-07-10
System>Administration>Software Sources


Tick 'Multiverse,' then back in the Terminal type 

```
sudo apt-get update
```
 

After that you can do the previous command.

---

### Post by Rabz on 2009-07-10
ok.. progress.. but.. how do i fix this? 

"407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied"

I did put in my authentication details and i AM surfing the net.. so whats it moaning about??

---

### Post by Martin Marshalek on 2009-07-10
If you don't want to mess with the terminal, you can also go into the Add/Remove Programs under the applications menu and search Ubuntu Restricted Extras (You may need to select all available software from the drop down list) . Then check that and install.

---

### Post by LowSky on 2009-07-10
> **Rabz said:**
> ok.. progress.. but.. how do i fix this? 

"407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied"

I did put in my authentication details and i AM surfing the net.. so whats it moaning about??

looks like your proxy is denying access to the ubuntu repos
[https://support.counterpath.com/default.asp?W24](https://support.counterpath.com/default.asp?W24)
> 

407 - Proxy Authentication Required

Error “407 Proxy authentication required” indicates that the client must now authenticate
itself with the proxy. This error is normal in networks where authorization is enabled (most networks) and can occur once per SIP request and is generated by the network. If you are continuously getting this error, either you have entered incorrect login information (username/password), or your account has not been provisioned or set up properly.

If you are using one of our retail products, verify that your account credentials have been properly entered. If the problem persists, we recommend that you follow up with your VoIP service provider.

---

### Post by 3rdalbum on 2009-07-10
Immediately after you install Ubuntu, the only software it knows about is the software that came with it on the disc.

You need to enable the software repositories in System > Administration > Software Sources, and after you've ticked the boxes and pressed Close, it will ask you if you want to reload the package list. Do it.

Then your codec search will work perfectly fine, or you can install the Ubuntu-restricted-extras package from System > Administration > Synaptic Package Manager.

I recommend installing the package from within Synaptic, NOT from the command-line unless you are familiar with using text-based GUIs.

URE contains most of what you need for a full multimedia experience, including Flash Player, Java, most codecs, and Microsoft fonts.

---

### Post by Wim Sturkenboom on 2009-07-10
> **Rabz said:**
> I did put in **my authentication details** and i AM surfing the net.. so whats it moaning about??I have never used Ubuntu in combination with an ISA server. So my question is where you entered the credentials? Did the package manager prompt you? Or did you enter them in firefox when firefox moaned?

---

### Post by moody_mark on 2009-07-10
Just a side note, You can change the proxy settings through "system" --> "preferences" --> "Network proxy" I have to swap that about on mine when im working on / off my work VPN for the Add / Remove or the package manager to work

---

### Post by Tender Prey on 2009-07-10
Hallo!
I'm very new to this forum and especially to Ubuntu.
I' just like to say that you are fantastic: if someone has a problem you are immediately ready to help him/her! Great!

---

### Post by A' Podartho on 2009-07-10
> **Rabz said:**
> ok.. progress.. but.. how do i fix this? 

"407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied"

I did put in my authentication details and i AM surfing the net.. so whats it moaning about??
OT, are you the same one on BC forum ?
if not, sorry.

---

### Post by A' Podartho on 2009-07-10
> **Tender Prey said:**
> Hallo!
I'm very new to this forum and especially to Ubuntu.
I' just like to say that you are fantastic: if someone has a problem you are immediately ready to help him/her! Great!
that's true, the linux gurus are really helpful.

---

### Post by aysiu on 2009-07-10
> **Martin Marshalek said:**
> If you don't want to mess with the terminal, you can also go into the Add/Remove Programs under the applications menu and search Ubuntu Restricted Extras (You may need to select all available software from the drop down list) . Then check that and install.
I agree, and I think this is particularly worth mentioning in the Absolute Beginner subforum.

Step-by-step instructions (with screenshots) here:
[http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

---

