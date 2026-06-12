---
title: "Beginner HowTo Server Setup for Small Office"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by casanova frankenstein on 2009-03-07
Beginner Forum,

I have a small, 2 person office that at present has no client/server arrangement and which has requested my services repeatedly in an MS-XP desktop environment. They have thousands of word documents which are being hosted locally on one of the PC's, are shared with both PC's, and which are vital to the function of their office.   

It occured to me that entrusting one of the end-users with all of these important word documents is probably not a good idea and it seems like it's time for them to advance from their present peer-to-peer networking to a client/server environment. 

I would like to install a Ubuntu server in this small office to accomplish this client/server file sharing. Later in the future, once a file server is working there are a few varied other tasks: a print server, remotely administering the server, remotely backing-up the server and remotely backing up the many word documents, and finally the capability for an end-user to access these word documents remotely from home. Its my understanding these other server applications could be installed at a later date. 

I believe this would require Ubuntu SSH, NFS, FTP and Print Server applications, possibly other server applications but I'm not sure what those might be. I searched the Internet, these forums and withdrew books from the library including the "Official Ubuntu" book but found nothing which directly discussed my concerns in a way that I understood them. I'm posting this inquiry here in the beginner forum because, although I believe I could install and administer Ubuntu server in this environment, I would be easily lost with a "Ubuntu Server Howto" set of instructions not written clearly or unnecessarily burdened with slang or insider jargon. At present, what I find particularly challenging is the terminal CLI and the meaning, proper usage and conventions for commands to accomplish the various tasks.  

I believe I already have most or all of the inventory of equipment to effect such project. I have an old Intel P111 to act as a server, but if too slow I have other, faster PC's. The 2 end-users reside on their own router/hub which has NAT, (native address translation), with the wireless component of the router disabled. The 2 end-users are the only users on this router/hub. The two existing PC's in this small office are notebooks which are installed with MS XP Pro. One of the notebook PC computers leaves the office environment regularly to be used elsewhere.   

I hope someone has seen or heard of such a Ubuntu Server HowTo and could point me in the correct direction. I can't stress strongly enough how lost I am with varied commands of the terminal CLI and would require the most assistance in this area. I tried to include as much information as possible to describe the existing small office environment and what I hope to accomplish but likely am omitting something I'm sure. It seems to me this would be a straightforward server install and for someone who's done this before, it would seem like someone knowledgeable could accomplish an install similar to this in a short afternoon. Not to diminish the significance of such a project, simply to indicate that I have gone as far as I can go on my own and hope someone can suggest where to go next. 

Thank you for your time. 
 
C.F

---

### Post by Ripose on 2009-03-07
Although a Windows Server is easier to use, a Linux Server if far more controllable (yeah I know you didn't ask);)

I assume you have looked into SAMBA?

It is far easier (less in depth control) to install the server on an existing Ubuntu OS, because you will still have a graphical interface.
SWAT may help too (Samba Web Administration Tool)

Also, for a somewhat automatic install of server choices: In Synaptic Package Manager - Click "Edit", Click "Mark Packages By Task", nice pop-up with several choices.

Sorry I did not really address your issues, I am in the process of doing something similar myself.

:D

---

### Post by casanova frankenstein on 2009-03-07
> **Ripose said:**
> Although a Windows Server is easier to use, a Linux Server if far more controllable (yeah I know you didn't ask);)

I assume you have looked into SAMBA?

It is far easier (less in depth control) to install the server on an existing Ubuntu OS, because you will still have a graphical interface.
SWAT may help too (Samba Web Administration Tool)

:D

I'm somewhat familiar with SAMBA and I'm nearly certain I could install a server with SAMBA to accomplish this. I haven't dedicated myself to any particular application or technology as yet, and if SAMBA is the preferred method to get the job done then I have no objections. I'm thinking an actual Ubuntu Server install may be the way to go, since at some point in the future I'd like to administer the Ubuntu Server remotely, there won't always be a monitor attached to the server-a GUI may be redundant, but since I don't know what I'm doing at the moment, I'm not including or excluding anything. 

My hope is to install and use the ideal server application for this project, keeping in mind the small office in question is in a professional environment and I'd like to incorporate in this small office what typically, conventionally would be installed to service the computing needs found in other professional environments. 

I'll take a look at the SWAT tool you suggest.

---

### Post by Xiong Chiamiov on 2009-03-07
You can uninstall the GUI from a normal Ubuntu install, or install one on Ubuntu Server; the only real difference that I know of is that the Server kernel has some different optimizations.

NFS is for *nix-to-*nix sharing, so you won't use that.  For sharing with Windows, you'll be using Samba.  I believe printer-sharing will use that as well.  I have a few samba-related bookmarks [here](http://delicious.com/xiong.chiamiov/samba) that you may find useful.

Ubuntu is very similar to Debian, for which there are *many* guides available on the web.  I find myself looking at articles from [nixCraft](http://www.cyberciti.biz/) often.

---

### Post by casanova frankenstein on 2009-03-07
> **Xiong Chiamiov said:**
> You can uninstall the GUI from a normal Ubuntu install, or install one on Ubuntu Server; the only real difference that I know of is that the Server kernel has some different optimizations.

NFS is for *nix-to-*nix sharing, so you won't use that.  For sharing with Windows, you'll be using Samba.  I believe printer-sharing will use that as well.  I have a few samba-related bookmarks [here](http://delicious.com/xiong.chiamiov/samba) that you may find useful.

Ubuntu is very similar to Debian, for which there are *many* guides available on the web.  I find myself looking at articles from [nixCraft](http://www.cyberciti.biz/) often.

Thank you for your input and suggestions, I briefly looked over the nixCraft site and it looks like it will be very helpful for various HowTo's. I'm of the firm belief that if the instructions are clear enough and easy enough to handle, I could do and build just about anything, a 747 airplane, open heart surgery, whatever. True genius is found in taking the very complex and presenting it in a manner that anyone can understand. I hope my little networking project doesn't rise to this magnitude of complexity, I don't think it does, but I haven't as yet found the HowTo manual that fits my needs. However I'll spend some more time with the nixCraft site and determine if its applicable, reporting what I find along the way. Thanks again for recommending it.    

As I mentioned, my achilles heel weakness is all the acronyms and insider jargon which everyone else seems to know but for me represent insurmountable obstacles. For instance, when talking about NFS, I don't know what "*nix-to-*nix" refers to. "nix" makes me think of an Ethernet NIC card, though I'm sure this is wrong. Further contemplation would seem to indicate that it should mean "Linux-to-Linux", though this confuses me further because it was my impression that NFS is a multi-platform server application. Wasn't NFS created before Linux even existed? You are the second person to suggest SAMBA to fit my application so maybe I should take this advice as this may be the preferred method. 

Appreciate your input.

Edit: Appeciate the suggestions so far. A little investigation indicates SAMBA may be the prefered server install and NFS in my application is neither ideal or recommended. Is this correct? 

If so the question now becomes a "HowTo" to install Ubuntu Server and SAMBA in a client/server arrangement with windows clients, evolving away from the peer-to-peer environment that presently exists. 

Hope I'm describing this correctly.

---

### Post by Kellemora on 2009-03-07
HI CF

SAMBA is designed for networking with Windows computers.

I may have this wrong, but Windows uses MBA protocol, 
SAMBA stands for Same As MBA?????  don't quote me on that, I didn't look it up.

In order to have Remote Administration, that would use SSH protocol.

I have 8 computers (actually 9) here in my office.  5 are Ubuntu Hardy 32 bit and one is Ubuntu Hardy 64 bit, two Doze XP machines for POS and one XP-Pro machine stand alone for accounting purposes.

I use SAMBA for office file sharing, having created a single folder on a dedicated machine simply named File_Server and all files are in sub-folders under that main file folder.
Not really a Server Server, just a shared folder that gets mirrored 4 times a day.
Having ALL the files on a single machine has greatly simplified our work!

But I'm a noob too and still have all the problems noobs have keeping things humming along.

Good Luck

TTUL
Gary

---

### Post by starcannon on 2009-03-07
C.F.

While a little dated, I believe [this walk-through]("http://www.howtoforge.com/ubuntu-home-fileserver") should do the trick for you; I would use Ubuntu 8.04 Server (the latest long term support version) instead of the 7.10 server that the guide mentions. I believe this will accomplish your short term goal comfortably, while giving you plenty of room to grow and provide additional server functions in the future.

GL

Rob 

[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

---

### Post by anewguy on 2009-03-07
EDIT:  Sorry - didn't notice the previous poster had already pointed you to this same how-to.


This link may help you in setting up the very basics of a server, from which you can grow into what you want.  I know the samba config file contains sections for printers, cd drives, etc..  This little how-to is easy to follow to get a server installed, then you can modify it to do what you want or at least to experiment a little to help you decide how you want to do your "real" server.  

[http://www.howtoforge.com/ubuntu-home-fileserver]("http://www.howtoforge.com/ubuntu-home-fileserver")

The samba config is also where you would set up user level accesses in combination with the username/password from Windows.

I used this to set up a very simple server at home, so I could try to learn the server environment.  It mentions gutsy, but it equally applies to 8.04 server which I used.

There are tools available to allow remote access - some like ssh will be command line based.  Others are browser based.  Some people would argue that it's best to use something cli based so really learn things - me, I don't know, I was able to get things done with a browser based tool

Hope this helps in some small way.

Good luck!

dave :)

---

### Post by linuxisevolution on 2009-03-07
I have some howto's on my site for setting up apache and similar things. Instead of re-writing it all, it is here:

[http://98.219.177.90/apache2-default/thelinuxhowto/The_Linux_HOWTO.html](http://98.219.177.90/apache2-default/thelinuxhowto/The_Linux_HOWTO.html)


Just click "apache2 server" on the side pane. :) Good luck.

---

### Post by casanova frankenstein on 2009-03-07
Thank you all,

With the forums assistance, I got past my misunderstanding of which server to use and now could more accurately describe what I hoped to accomplish in this small office. 

While I haven't thoroughly looked into all of your suggestions, it seems that starcannon's Ubuntu Samba walkthrough may more closely fit my situation. This walkthrough is step-by-step and seems easy to read, it does contain initially some confusing parts, but I will endeavour to persevere in my own indomitable fashion, no doubt making ample mistakes along the way.

I think I'll create a "mock-office" Server install here at home before I attempt it elsewhere.  

Thanks again everyone,

CF

---

### Post by MrWES on 2009-03-07
I would like a similar setup. I have a desktop running Ubuntu 8.04 Desktop on one 160GB drive. I'd like to replace that with the 8.04 server and run it headless, as I mostly use my laptop running 8.10 Intrepid, and my wife uses another laptop running Windows XP. 

Can I split up the server hard drive this way?

server / - 10GB formated ext3 -- running SAMBA
server /data - 149GB formated NTFS
server /swap - 1GB

I understand the laptop running XP will be able to read/write to the NTFS partition with SAMABA, but will the laptop running Intrepid be abel to read/write to that partition?

Recommendations and feedback wanted.

Thanks,
Bill

---

### Post by starcannon on 2009-03-07
Yeah you will be able to read and write to that partition from Ubuntu as well.
In Ubuntu you would:

[LIST=1]
[*]Click Places
[*]Network
[*]Choose the file server
[*]Provide any credentials required by your security settings.
[/LIST]
That ought to do it.

GL

---

### Post by MrWES on 2009-03-07
Sounds good.

On the Windows XP laptop, do I 'connect' to that server on startup/login, or just mount the shared partition?

And can I connect to that server automatically, or do I need to point Nautilus to it everytime?

Last question; will Ubuntu server detect and install my printer for me? Or do I need to run the CUPS configeration say from [http://localhost:631](http://localhost:631) ? The HP printer is supported as I have it already running with Ubuntu desktop.

Bill

---

