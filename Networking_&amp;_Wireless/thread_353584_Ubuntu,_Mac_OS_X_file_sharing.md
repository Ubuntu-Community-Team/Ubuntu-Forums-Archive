---
title: "Ubuntu, Mac OS X file sharing"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by Oblivion Knight on 2007-02-04
I'm a bit of a novice(that doesn't mean I'm stupid) to Ubuntu(currently I've got 6.10) and I need some help setting up file sharing on an LAN between my laptop(Ubuntu) and a eMac OS X. Could someone help me out with a decent list of instructions(and a list of commands to reverse the changes)? Any help is greatly appreciated.

---

### Post by etienne.navarro on 2007-02-07
It's quite easy to setup a share on OS X.
Click on System Preferences --> Sharing. Make sure the Services tab is selected. Choose one of the sharing methods, either UNIX sharing or Windows sharing.

On your Ubuntu machine, go to Places --> Connect to server and enter the sharing details.

---

### Post by PCVRX650linux on 2007-03-01
> **etienne.navarro said:**
> It's quite easy to setup a share on OS X.
Click on System Preferences --> Sharing. Make sure the Services tab is selected. Choose one of the sharing methods, either UNIX sharing or Windows sharing.

On your Ubuntu machine, go to Places --> Connect to server and enter the sharing details.

This thread is getting older, so I may not get any responses, but I'll try here first. I, similarly, want to share files between a Mac and a Ubuntu machine. The mac is running 10.4.8, and the linux is running Edgy. They are both on the same wireless network. I followed your instructions on my mac machine (although UNIX sharing was not an option, so I just selected Windows, is this correct?). On my Ubuntu machine I'm not sure what kind of sharing details I need to put in. Browsing I don't find the mac. I've got very little experience networking. Setting the Ubuntu machine up as a file server would be great if I could pull it off.

---

### Post by etienne.navarro on 2007-03-01
The network browsing in Ubuntu sometimes sucks so you might not see your Mac.
The windows sharing setup on your mac should be fine. First test that the sharing is working. Open a nautilus window (like Places --> Home) and in the address bar type
```
smb://*ipaddress_of_your_mac*
```
If it connects then you can make it a permanent share by going to Places --> Connect to Server.
Specify a Windows share, server is the ip of your mac, you can also fill in the other information accordingly.

---

### Post by svenand on 2007-03-06
Here is a description on how to setup file sharing between Ubuntu Linux
and Mac OS X when they reside on the same machine.

[http://svenand.blogdrive.com/archive/14.html](http://svenand.blogdrive.com/archive/14.html)

---

### Post by jonkulp on 2007-12-30
I'm pretty new to Linux also, having about a month with it so far.  I'm running 7.10 on a laptop using a wireless network connection, trying to connect to my eMac, which is wired with an ethernet cable.  I managed to connect and share files (from laptop to eMac, but not the other way around so far) in two different ways. 

First, on the eMac I enabled the "Windows Sharing," "Remote Login - SSH,"  and "FTP access" sharing options.  When you highlight each type of sharing by clicking on it, it tells you how to connect to the computer using that service.  For example, when I clicked on "Remote Login - SSH," it told me to type "ssh Jon@10.0.1.2" at a command line.  I tried this on the laptop and it prompted me for my password (my eMac password), which I typed and got a nice welcome to Darwin message.  I was able to view my eMac's files using the few basic shell commands I know like ls and cd and so forth.  I tried copying a file from the eMac to the laptop but I must have typed something wrong.  I'm pretty new at this and I really need a GUI to do any file transfers from one machine to another.  

I couldn't figure out how to make a network connection with Nautilus at all.  The eMac didn't show up and Nautilus didn't find it when I tried typing in the 10.0.1.2 location either.  I thought I'd try the FTP method, even though I haven't seen any forum postings on it to see whether it works, and it worked great for me!  I opened up FileZilla, which I have used a few times for updating my website, and typed "10.0.1.2" in the "host" field, then "Jon" as username, then put my eMac password in the password field and hit return.  It connected immediately and showed my eMac's files in a frame on the right side of the window.  From there it was easy to drag-and-drop whatever files I wanted onto the laptop and vice-versa.  Hope that helps somebody else too.

---

