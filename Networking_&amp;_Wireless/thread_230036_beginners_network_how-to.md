---
title: "beginners network how-to"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by oliwally on 2006-08-05
I've been going through this forum for hours and cannot find a 'total beginners network how-to'.

I would simply like to network my Kubuntu labptop with my Kubuntu Desktop so I can share files (and an internet connection). At present both computers have internet through a modem connected to a small hub. I was able to configure this kind of networking in WinXP (dual boot on both computers) without any major probs, but I just don't know how to even start in Kubuntu. I need step-by-step instructions.

Could someone please point me to an existing thread or how-to or anything that will enable me to get this going. Alternatively could someone perhaps give me step-by-step instructions in this thread?

Thanks in advance.

---

### Post by spd106 on 2006-08-05
You need to set up a server on each of the PCs to allow file sharing. This is due to the more secure nature of ubuntu (ie no open ports). You have a great many choices, there's samba, nfs, ssh, ftp, http, webdav...

For a beginner I would start with samba since this will allow you to easily share files with windows PCs. Have a look in the wiki for a guide to setting it up. You will need to install the server and edit the smb.conf file. I believe there have been discussions about a settings gui, but I haven't used one yet.

Here is the community docs page, I would advise a read through first.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by oliwally on 2006-08-08
Thanks for that - it helps a little. Samba seems to be the most straight forward and plenty for what I need.
Has anyone spotted other, more precise how-tos, specifically for KDE?

---

### Post by Mooie on 2006-08-08
for connection sharing i think i saw an option in the program "Firestarter" (a graphical frontend for the firewall) to enable connection sharing. you can get the program via synaptic

---

### Post by oliwally on 2006-08-20
Hmmm... I'm still looking for a user friendly, step-by-step, gui based how-to to help me set up the file sharing between the two computers.

I've found some information on how to do this by using a text editor to edit smb.conf, but I'm convinced that it must be possible using guis, right?

Has anyone seen a simple how-to on this, or can someone very tricky perhaps make one (please)?

---

### Post by oliwally on 2006-08-22
I'm still looking ;)

---

### Post by RageAgainstThis on 2006-08-27
I hate to say this, but i think simply learning how to edit the samba.conf is your best way to go.  I was in your situation a couple weeks back when i jumped on the linux train.  But once you read through the config file, you should be able to get a grasp on it.  There are tutorials here and there for it.

---

### Post by petri on 2006-08-28
Well, there is a one good one on [Linux NFS-HOWTO]("http://nfs.sourceforge.net/nfs-howto/index.html")

It does contain a lot of words and it's not gui based. It took me a half an hour to fix my previous NFS-installation and I am an novice so take a look at that HOWTO. Remember, you do not have to read everything in that HOWTO ;)

BTW have you tried just to share folders with NFS? (It will install the NFS automaticly, kind of.) That's gui and should work. If it doesn't the howto above will fix it. Just copy and paste in terminal and you don't have to worry about is it Ubuntu och Kubuntu :cool: 

P.S. Use samba only if you have to share files and folders with windows and/or linux. Use NFS if you only share with linux. But you can use both if you like/need to. [Here]("http://www.ubuntutorial.com/?p=5") you can find a samba with step by step and gui...

---

### Post by oliwally on 2006-09-01
Wow, thanks for that petri. Very much appreciate the help. I wish there was a KDE version of the [how-to]("http://www.ubuntutorial.com/?p=5") you pointed me to. It's a good one!

I have also discovered that, after installing samba, not too much more work was required. Someone pointed me to a 'shared' folder has been created in my home directory, and that I should be able to access that from my other linux computer. It was correct! The default samba configs (almost) worked. Just had to make sure that both computers were configured similarly.

I'm still hazy on the details though. Why, for example, does it take 3 or so minutes for the two computers to recognize each other? What exactly does smbpasswd do? I haven't set a password and it works anyway, is that a problem?

---

### Post by nikkkko on 2006-09-01
> I wish there was a KDE version of the how-to you pointed me to. It's a good one!
You're not the only one.

I have four boxes running kubuntu and no windows.  They share an adsl connection and the network is part cable, part wifi.  Everthing works fine, (well, wireless was a bit of a dog to get going), and the machines can all ping each other, but can I get sharing sorted the way I want?  Not from the gui.

IMHO, sharing via the gui is a disaster.  NFS may be universally recommended for a Linux only environment, but there is absolutely no documentation about how to use NFS under the Kubuntu/KDE gui.  You may be able to click on a 'Share' tab and select NFS, but then what? You can fiddle with the 'Sharing' settings in 'System Settings', but what do they do?  You won't find one jot of information on the Kubuntu site and there's nothing on the KDE site either.  Go figure.

---

### Post by nikkkko on 2006-09-01
Oops.  Double posted (how do I delete this..?)

---

### Post by petri on 2006-09-02
KDE might be big but in Ubuntu gnome is bigger. Everybody (who knows Linux) is posting the commands you can copy and paste in Terminal so I recommend you to use it and accept it.

Otherwise you will miss a lot of help from these forums and that is not fun. Although there is a nice Linux magazine and quite a good price too (free) and they are KDE guys: [http://www.tuxmagazine.com/](http://www.tuxmagazine.com/)

EDIT: There is actually one article on Tuxmagazine nr 2005/5 Dancing with Windows :D with some pictures. I don't know if it is helpfull but give it a try.

---

### Post by nikkkko on 2006-09-02
> Everybody (who knows Linux) is posting the commands you can copy and paste in Terminal so I recommend you to use it and accept it.
Of course you're right.  

Like everyone else I installed the nfs utils, edited exports, hosts.deny and hosts.allow files and have sharing working how I want - much of my newly aquired knowledge gleaned from these very boards.  What I'm complaining about - not really a complaint seeing as Kubuntu is free and meets 100% of my computing needs, more a mild sort of gripe - is that gui NFS is part of the Kubuntu package, appears not to work and yet there is no documentation anywhere to figure out what's going on.

(Now if I can just get my wireless to connect before the system tries to mount my remote shares I will have reached network nirvana).

---

### Post by petri on 2006-09-02
About beginners nerwork howtos there is one more I know:

[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

It uses SSH for networking, interesting.

But just guess which desktop environment it shows :-\"

---

