---
title: "Windows File Browsing Not Working Out-of-the-box"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by Yfrwlf on 2007-01-19
Everywhere I've read users are saying that all you have to do to see Windows shares on your roommates computers who won't switch to Linux is open Network Servers in Places, then Windows Network, then you see all of them and everything is magical with butterflies and unicorn giggles.  It's not happening for me :(

The other computers can see each other fine, but I can't see them.  I have Firestarter running but I tried stopping it and it didn't help.  I also set it to allow ports 137-139 and 445 through.  Since you don't need Samba to see other computers, I don't know what conf file I could paste to be of help.  I can ping the other computers, I've tried both manual and automatic DHCP for my network settings, nothing will let me see the other computers on the network.  Maybe I'll just do a fresh install, even though I don't see what I could have done wrong to mess it up.

Does anyone have any ideas of anything I can check to find out why I can't see other Windows file shares?  Any suggestions at all would be very helpful.

Thanks :grin:

---

### Post by meng on 2007-01-19
Are you accessing by hostname or by IP address? I find it's easier to access by IP address.

---

### Post by Yfrwlf on 2007-01-19
> **meng said:**
> Are you accessing by hostname or by IP address? I find it's easier to access by IP address.

I tried putting in smb:///192.168.1.105/ and that did not work either, if that's what you mean.

---

### Post by meng on 2007-01-19
I assume you entered
smb://
and not
smb:///

:D

---

### Post by Yfrwlf on 2007-01-19
> **meng said:**
> I assume you entered
smb://
and not
smb:///

:D

No, I thought it was some kind of special triple-slash thingymobobber >.<  Thanks a bunch.

Do you know why, though, I can't automagically see other shares?  It's wouldn't be because I need to place myself in same workgroup would it?  That would be silly, if that were the case, because then there should be another level that shows you all the visible workgroups.  I've read that everything is viewable to other users by default normally, so I don't know why I'm the exception.  They are not using the standard MSHOME though if that has anything to do with it.

Thanks a ton for the easy fix, though. =D>

---

### Post by meng on 2007-01-19
If you have static IPs, you can change the /etc/hosts file to provide a hostname/IP translation table. You can also use this guide to automatically mount your partitions at boot and potentially save you a lot of trouble in future:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

If you don't have static IPs, well then there's probably still a way to achieve it (but I'm not sure how).

---

### Post by Yfrwlf on 2007-01-20
> **meng said:**
> If you have static IPs, you can change the /etc/hosts file to provide a hostname/IP translation table. You can also use this guide to automatically mount your partitions at boot and potentially save you a lot of trouble in future:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

If you don't have static IPs, well then there's probably still a way to achieve it (but I'm not sure how).

Thanks a bunch for responding and for your help. :)  Just a thought, but if you do get Samba configured correctly, you can use Samba for automatic share discovery.  I wonder if you had it set up, if you could then see the shares using Nautilus.  In any case, I seem to be unable to set up Samba because messing with all the options in the Samba conf is way too complicated for me, I've tried it, and the only way I've figured out how to do it is by using the nice Samba configuration tool that Fedora comes with.  It's very simplified and has what I need to get it working painlessly, while the tools available in Ubuntu are way too complicated with things that I know nothing about.  I really hope that in Feisty Fawn they integrate Samba further into things so that sharing and viewing files is easy to do in "simple mode".  Provide the simple Samba configuration needed to have others access your files you share out with no password, and also provide a way to require a universal password.  (the option for a unique password for different folders, and for listing which users can view it would be nice too)  Basically, I'm saying Ubuntu needs a Samba config tool like Fedora's, because it can do all that very simply.  All someone needs to do is port it over, something I have no concept of doing (yet).

It's a re-occurring theme in Linux, in fact.  Lots of different developers give a billion options in a program which makes it very powerful and customizable, but then users come along who just want simple functionality and they are faced with screaming and running away, or learning the whole thing and becoming experts just to get that *simple* functionality from the program.

I think one of the reasons Windows is successful in some ways is it uses both simple options for normal users, and advanced options for advanced users to configure things further.  Unfortunately, these "advanced options" are often so convoluted that not even MS employees know what they hell they are for.  Registry keys can be exterminated from this earth. =P  So Linux is often much more powerful because power users can actually *use* it since things are often well-commented (in most cases I think) unlike Windows.  It just needs to provide those *simple* tools for users who just want things to work in "simple mode", while not getting rid of the tools to make things work in complex and powerful ways.

---

### Post by Yfrwlf on 2007-01-20
Or is it supposed to work out-of-the-box too? =P  From what I've read, installation and configuration of Samba has to be done manually, so I just hope in Feisty it's must easier than that. :wink:

---

