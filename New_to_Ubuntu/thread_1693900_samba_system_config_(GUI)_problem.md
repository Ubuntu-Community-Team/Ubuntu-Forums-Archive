---
title: "samba system config (GUI) problem"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by winlinconvert on 2011-02-23
Hi All,

Am new to Linux and have just installed Ubuntu netbook 10.10 on a compaq mini 110 and I must say that I am very impressed to date. I have installed the GUI version of samba system configurator, as per instructions on the unixmen website, but it does not seem to run.  I get asked for my password then nothing, no boxes, windows, nothing?  I have tried to re-install but it has the same effect.  Any suggestions would be very welcome.

Many thanks.

---

### Post by gordintoronto on 2011-02-23
Here is my suggestion: open Administration/Synaptic Package Manager, and search (not quick search) for the package. Select it, then click "apply" to install it. If it's not found, don't use it. In Windows, you download stuff from the Internet and install it. In Linux, we try to avoid doing that.

I have used Samba in several versions and distros of Linux, and I have never, ever had to do anything to configure it. It "just worked."

Your objective is to share a folder on your Ubuntu machine, or you want to access a Windows shared folder, or both. I do both. Let me know, and I'll explain how I do it.

---

### Post by winlinconvert on 2011-02-24
Hey Gordintoronto, thanks for the reply.  I wanted to use the GUI as I have no experience with Linux/Unix commands (only DOS), but am happy to learn.  I have tried the Synaptic Package Manager but to no avail.  I couldn't find anything under Samba System Configurator.  I'd very much appreciate any help configuring Samba/Windows to be able to share files and the printer.  An overview of my home system is as follows;

Dell Dimension 2400 with Windows XP sp3 as print server with Canon Pixma MX870.
HP Pavilion Slimline media centre with Vista sp2
Acer one netbook with Windows 7 starter
Compaq Mini 110c netbook with Ubuntu 10.10

Everything connected wirelessly through Orange Livebox ADSL home hub.

The Windows machines all see each other and I can share files & printer.
The Vista machine can see the Ubuntu netbook but shows it as "unknown device".
The Ubuntu netbook can see & access everything except the printer!

---

### Post by gordintoronto on 2011-02-24
If I have read your message correctly, you want to access the printer, and that is the only issue. Open Administration/printing and click "add". Select "network printer" and wait a few seconds. I would expect the Canon to magically appear, and you could select it.

That's what happens with my Brother laser printer, which is attached to my router. I play around with various distros/versions, and they all can print after a few mouse-clicks.

---

### Post by winlinconvert on 2011-02-27
Thanks for the guidance.  I followed your instructions and located the printer.  Then I had to find and load the relevant driver, which was not in the supplied PPD database, but having done some research it is now working perfectly!

The only other issue now is getting the vista machine to recognise Ubuntu on the network, so as I can set up file sharing permissions on the vista machine. Currently vista shows the Ubuntu machine as "unkown device" and wont give me access to it.  My basic understanding of Samba is that you don't need it to view and share files on a windows home network but is this the same for windows clients wanting access to files on the Ubuntu client? Is there some tweaking of Samba or vista needed?

---

### Post by Ben Page on 2011-02-27
You need to configure your SAMBA server to be in the same workgroup/homegroup as Vista. Check your workgroup name in Vista (computer properties) and then add the workgroup name to your /etc/samba/smb.conf file, or trough the system-config-samba GUI in preferences> server settings. You have to share the folders/files in order to Vista have access to them.

---

### Post by Morbius1 on 2011-02-27
I think we need some facts. On the Ubuntu machine post the output of the following commands:

This one will show the Samba usershare ( aka nautilus-share ) shares you may have created on your Ubuntu machine:
```
net usershare info --long
```
This on will show your samba configuration as well as any Samba Classic shares you have defined:
```
testparm -s
```
This one will output a list of every workgroup on your LAN and within every workgroup every host and within every host every share. It may also output some incoherent but useful error messages if something is wrong:
```
smbtree
```

---

### Post by winlinconvert on 2011-03-03
Thanks for the info Ben, got it to work after a bit of playing around. Cheers.

Morbius1, thanks for the CLI commands.  The smbtree threw up an interesting message as below:

WORKGROUP
	\\STEVESCOMPAQ   		
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED

The rest of the LAN on the other two PC's listed ok.

All, going back to my original post above,  I managed to get the Samba GUI to work by restoring the original unmodified smb.conf file.  The Samba GUI would then run quite happily, but when I go back to the modified smb.conf file, modified by the CLI, then Samba GUI does not run.  Interestingly, I have now junked the Samba GUI for CLI as this actually seems to work better and gives me more flexibilty.

---

### Post by winlinconvert on 2011-03-06
Found that certain errors in smb.conf will stop the Samba GUI from running.  So use of testparm after any modification to smb.conf is essential to edit out errors.  Having now "cleaned up" my working smb.conf the Samba GUI runs quite happily.

---

