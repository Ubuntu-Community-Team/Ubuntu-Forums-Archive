---
title: "Samba Not Working"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by flowingfire on 2007-05-10
Hi Everybody,

I'm having some trouble with Samba.  Being a new Linux user just coming over from Windows I don't know a lot about how to make this work.

I installed Samba... And I managed to set up my printer and some folders for sharing.  But the workgroup I set up doesn't show up on any of the Windows computers in my house.  It doesn't show up to the Ubuntu computer, itself, for that matter. I can access any other Windows computer's shared files, but not Ubuntu's on samba. 

I have installed, re-installed, and tried various configurations, tried making the workgroup Mshome... Nothing seems to make it work...  Help!  I just want to share my printer and my music and stuff.

I've been using Ubuntu for a couple of weeks now, and I want to make it my primary operating system instead of Windows... But this is way too hard right now.  If I can get this working and never have to think about it again, I would love that... 

Thanks,
-David

---

### Post by GolfGeek on 2007-05-10
Dave
Try searching for the thread  202605. There is a great how-to on setting up Samba and integrating with p2p network. I am new to this myself but this guide does a great job and it does work. I am still having a few issues but the basics are there and I'm plodding thru the rest

---

### Post by AlanR8 on 2007-05-10
I posted the below in another thread. I was having EXACTLY the same issues so this is what I did.........

I'm fairly new to all this, an old Doze hand and Linux of various flavours since Christmas 2006, finally settling on Kubuntu with the pre-release of Feisty in March.

I've now got three K boxes and and one XP box that I dare not swap for fear of a slow and lingering death at the hands of my wife. It's her machine.

This weekend I set out to get the networking sorted, and whilst it took a while, once I'd cracked it things are quite logical. I could always see the XP box from the K boxes but initially the Ks were not showing in the Workgroup. What I did to make things easier was went to Synaptics and made sure I had the following installed:

samba
samba-common
smbldap-tools

As I recall, I had to download samba and the tools. They were NOT installed by default.

Next I went to [http://www.webmin.com/download.html](http://www.webmin.com/download.html) and downloaded the Debian version of this incredibly useful tool that works in your browser of choice.

Read the download instruction as there's a warning there that Webmin might complain about missing dependencies and it provides the apt-get to sort the problem.

Once Webmin is fired up in your browser, at [https://computer_name:1000](https://computer_name:1000) go down the menu on the left and select "Servers" then "Samba". You now have a graphical interface to work with. You can now make your selections, alter folder permissions, create shares and a lot more. Scroll to the bottom of the page and with a single click you can restart your samba server.

Webmin makes the alterations you need in your smb.conf file automatically and all should be well. However I did find a couple of things to watch out for and I'll share them here.

I picked up in these forums that you CAN'T log on twice to a 'buntu box with the same user name. The way around this is to make sure you allow "Guest" login and again this can be done in Webmin.

You'll see there's a password that's looks pre-populated and it seems to be your existing main password. If that suits, and I suggest it will, save any changes. I'd RECOMMEND you then look directly at the smb.conf file. Again it can be done directly from Webmin, and make sure you have guest = yes in the file and that the line is NOT commented out with a ; or # symbol.

Restart samba and you should be in! I can now read and write XP to Kubuntu, Kubuntu to XP and Kubuntu to Kubuntu. In other words, as it should be.

Good luck

Alan

PS Hope it helps

---

### Post by GolfGeek on 2007-05-10
Fantastic. I'll have to get back to the office to get webmin and try it. The great things about these forums is that someone else has run into the sadme problems. Tanks again

---

### Post by dmizer on 2007-05-10
don't know why you should need webmin unless you're dealing with a pure server.  even then, your best bet to get your shares configured correctly is via command line.

have a look at the first link in my sig.

---

### Post by flowingfire on 2007-05-11
Hi everybody.  Thank you so much!  I was able to get my music shared over my home network with extreme success.  Now I can be in another room on a Windows laptop and access music through linux on another parition entirely.  LOL.

And your help getting samba working made it all possible.  By the way, I find Webmin to be a fairly helpful tool. There certainly are other ways to accomplish what it can do, but for a new user who just wants things to work, it's helpful.

Of course, I didn't get the printer working... Hmm.. I think I'm going to post a new thread about that.  

See ya!

Peace,
-David

---

### Post by dmizer on 2007-05-11
a few words of caution:

there's no doubt that webmin is a helpful tool.  i use it myself on all my servers.  but you should use webmin with extreme caution.  not only is it helpful but EXTREMELY powerful.  with one or two wrong clicks you can render your ubuntu install completely useless.  also, unless configured correctly, it also makes your machine's root privileges directly accessible from any other computer on the network it's attached to.

i'm glad to hear you got things working the way you wanted, but please do not rely on webmin as your primary ubuntu configuration tool.  in the hands of a new user, it can be disastrous ... especially on computers that travel to other locations.

being useful, easy, and/or helpful doesn't necessarily mean that it is your best answer to a problem.

in this case, webmin's purpose is as a remote configuration tool for dedicated servers residing behind a firewall or secure vpn network.  it is NOT intended as a configuration tool for a desktop workstation because it's too powerful.

---

### Post by scradock on 2007-05-11
just a quick note - I was having the same sort of problems with samba connections to my WindowsXP machine after upgrading to Feisty.

With Edgy, everything on the Windows box was accessible, no problem setting up the connection to be read/write. Upgrade to Feisty - I could see the Windows stuff, and read from the shares, but not write to them.

After messing around (dangerously!) with webmin, installing samba again, editing smb.conf by hand (even more dangerous!) I realised that the connection was being refused by the Windows machine.

Solution - open port 445, MS authentication  - in the Windows firewall. Now it all just works. It looks as if a default changed in the upgrade, either to Feisty or to samba 3.0 - now it expects an authenticated connection to WinXP.

Hope that helps someone!

scradock

---

