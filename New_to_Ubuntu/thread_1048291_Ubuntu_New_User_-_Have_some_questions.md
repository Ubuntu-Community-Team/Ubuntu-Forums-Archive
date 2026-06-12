---
title: "Ubuntu: New User - Have some questions"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by StarsFan4Life on 2009-01-23
I finally came around and decided to jump into the world of Linux. I guess you can call Ubuntu Linux because of it's kernell, but it is very easy to use. 

I have a couple of questions regarding backups, access and applications for Ubuntu. I look forward to learning from the pros here and hope to eventually return the favor. 

First question: 

I installed Ubuntu on a Dell Latitude X300 (one of those mini laptops with a cd-rom) and it runs GREAT! I am really surprised at how well it handles everything I have thrown at it with only 1gb of ram. With that said, I am having troubles accessing files/folders on my home network via my WHS server. I have a share setup at \\svrhomewhs\media with access to all of my pictures, music, videos, etc on my WHS server. I love WHS btw...still running the trial and hope when the time comes I can just purchase a key and carry on. My question is, how can I have a permanent mount/map of \\svrhomewhs\media in Ubuntu so I don't have to manually access that folder all the time? I am not really familiar with "commands" with Linux so please bare with me. 

Second question: 

Can I utilize the backup feature of WHS to backup my Ubuntu machine? On Windows I have to install certain software so the backups can run. Can this be done with Linux as well? 

Third question: 

What free applications do you guys recommend I download and use with Ubuntu? I installed VLC lastnight but then fell asleep due to a head cold...but wanted to keep going. 

Any advise on Ubuntu in a Windows network environment would be greatly appreciated. I hope you welcome me with open arms.....

---

### Post by LowSky on 2009-01-23
I know nothing of WHS. but for question 3 I can help

Under applications there is add/remove
UIt has a giant list of all these great applications that are free.

---

### Post by billgoldberg on 2009-01-23
My advise is install samba.

--

I have no idea what WHS is.

---

### Post by lykwydchykyn on 2009-01-23
> **billgoldberg said:**
> My advise is install samba.

--

I have no idea what WHS is.

You shouldn't need to install samba; the laptop isn't going to be a server.

WHS is [Windows Home Server](http://en.wikipedia.org/wiki/Windows_Home_Server).  I know zip about it, but I can tell you now that if it came from Microsoft, it probably does not support Linux clients.  What's the actual name of the backup program?

As far as programs, what do you want to do?  LowSky is right, go to add/remove programs.  Don't go downloading stuff off the web, you'll end up frustrated trying to compile something from source when you don't need to.

---

### Post by BDNiner on 2009-01-23
To add a permanent map to the windows share you would have to add an entry to /etc/fstab. here is an excellent page from the ubuntu help website on mount the share:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by StarsFan4Life on 2009-01-23
WHS = Windows Home Server

What is Samba exactly?

Thank you guys for your help so far!  I am impressed with the quick responses!

---

### Post by hyper_ch on 2009-01-23
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by BDNiner on 2009-01-23
Samba is protocol that enables windows and UNIX like computers to talk to each other to share data and print services.

---

### Post by Coreigh on 2009-01-23
If you spend enough time with Ubuntu you will find that you will abandon WHS in favor of Ubuntu! In the mean time to create a more permanent mapping from Ubuntu you need to edit your fstab. The fstab file is the file that configures what points to where (as far as disks) at boot time. The fstab is found in /etc and when you can open it with gedit, but you need to be sudo (superuser) to make changes. To do this press alt+F2 to get the "Run Application" and enter "gksudo gedit" (no quotes) you will be asked for a password, use your normal Ubuntu password. Gedit will open and then you can open /etc/fstab, it will look similar to this:
> # /etc/fstab: static file system information.
#
#<file system>					<mount point>	<type>			<options>				<dump>	<pass>
proc						/proc			proc		defaults				0       0

# /dev/sda2
UUID=0cb89576-903f-42b4-be33-bef7d90910c4	/			ext3		defaults,errors=remount-ro		0       1

# /dev/sda1
UUID=80246E6D246E65DE				/windows		ntfs		defaults,umask=007,gid=46		0       1

# /dev/sda5
UUID=83782710-04c0-404b-8df4-10ef019e0270	none			swap		sw					0       0

/dev/scd0					/media/cdrom0		udf,iso9660	user,noauto,exec			0       0
/dev/fd0					/media/floppy0		auto		rw,user,noauto,exec			0       0
//whs/software				/mnt/R			cifs		rw,username=me@mydomain,password=mypasswd	0	0


That last line is the one you need to create. The first part is the server and share, change whs to the name of your server and software to the name of your share. Username me@mydomain, where me will be the username that you log into whs with and mydomain is the domain or workgroup name that the whs is serving. and of course password for that user. You are likely familiar with these things because you have already connected to the share but you just want to make it connect automatically at boot time.

Regarding the back-up, I have to agree with others that it is not likely WHS will "play nice" in backing up your Ubuntu files. But you can manually copy the files to the WHS share and have them backed up there.

---

### Post by lykwydchykyn on 2009-01-23
> **StarsFan4Life said:**
> WHS = Windows Home Server

What is Samba exactly?

Thank you guys for your help so far!  I am impressed with the quick responses!

Samba is, in a nutshell, a Linux/Unix port of Microsoft networking protocols -- file sharing, domain authentication, etc.  The client-side parts of samba (the stuff for Linux to interact with a Microsoft server) should already be installed (which is why you can browse that remote share).  Installing the SAMBA package would give you the server side of it, which you don't need.

I am certain there is an easier way to permanently mount SAMBA shares than monkeying with the fstab.  I'm not familiar with GNOME's tools, though, so I can't help you there.  If nothing else, you can create a folder in your home directory and then add a mount command to your startup commands, something like this:
```

smbmount //server/share my_folder

```

I know that's vague, but I'm not familiar with the more user-friendly methods out there.

---

### Post by linux6994 on 2009-01-23
Welcome to Ubuntu!

Samba is the package that is used to share files with the Windoze world. When you share a folder on you Ubuntu PC you will need to install Samba, as you set the share via properties it will install what is needed. I have found that file sharing is easiest handle through a GUI such as
system-config-samba "sudo apt-get install system-config-samba" in a terminal window this will give you a Samba entry in System> Administration >Samba that will you to assign a folder for file sharing.

To see the WHS you should just be able to go to Places > Network > Windows Network and see the shared folders. Remember that both PCs need to be in the same workgroup. The default workgroup in Ubuntu is WORKGROUP.

Good Luck!

---

### Post by egalvan on 2009-01-23
>  install samba.


The OP states that he:

[I]...have a share setup at \\svrhomewhs\media with access to all of my pictures, music, videos, etc on my WHS server

[/I]
His question is:

*how can I have a permanent mount/map of \\svrhomewhs\media in Ubuntu so I don't have to manually access that folder all the time*

My question is, how does intstalling Samba help automate the process?
If he is able to manually access Windows, isn't enough of Samba already installed?

---

### Post by Coreigh on 2009-01-23
Regarding the title of your thread, it is better to indicate in the title what the question is about. However it is common for new users to have several questions and many of us know what to expect when a "noob" starts asking some of their first.

That said, it is NOT ok to start a thread with something really generic like;
"PLEEEEEEASE HEEELLLLPPPP! I FREAKING OUT HERE!"

Either state the question or state the fact you are new and have several questions. Even then it is often better to ask all the questions separately, you will get more thorough answers.

---

### Post by StarsFan4Life on 2009-01-23
Noted by all on the subject title being so generic.

---

