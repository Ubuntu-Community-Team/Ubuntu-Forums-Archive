---
title: "There is no application installed for executable files"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by dannyboy75 on 2009-12-28
Hi all

Am a Windows sysadmin by trade, but I'm trying to get a bit more familiar with Ubuntu (9.10 specifically).

Installation was easy, but I'm having problems trying to install Eset Antivirus for Linux Desktop  ([http://beta.eset.com/linux](http://beta.eset.com/linux)) - it's a .linux file, but when I try to run it it says "There is no application installed for executable files".

Someone suggested I install Wine, but I thought that was for Windows executables? Tried it anyway, but sure enough it didn't work.

If  anyone can point me in the right direction I'd really appreciate it

thanks :)

Dan

---

### Post by mlentink on 2009-12-28
I am not familiar with the software. It is somehow alien to me to pay for antivirus software on Linux. I suppose you're installing on a server?
It is possible that the .linux file is a script that needs to be set to be executable with chmod +x filename

---

### Post by steveneddy on 2009-12-28
Why do you feel that you need an anti-virus application on your new Ubuntu machine?

Is this application available for Ubuntu? 

There are virus application in the repos that are used by many on the forums, but most of us don't feel the need for any virus protection.

Look at ClamAV.

```
sudo apt-get install clamav
```

[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)


EDIT:

Why would you want to use a BETA application for virus scanning?

If you chose to use virus scanning software on your Linux box then use something that has a proven track record and is used by most of the community.

Remember that the best way to get quality software is probably to ask us here on UF first before trying to install what could be a potential virus or Trojan threat in itself.

Problems arising with people coming from the Windows world is that they sometimes will install anything, just like they did on Windows, and expect everything to be OK.

Only install software from trusted sources. The Ubuntu repositories is probably the best place for secure software and there are some PPA's that have great software that are trusted.

Also, look at the links in my sig and search for anti-virus software.

---

### Post by WakkiTabakki on 2009-12-28
The problem is that when you downloaded the file, it didn't get saved with executable permissions (which is by-design)... 
The somewhat cryptic message you get means that, since it's not allowed to run the executable file, it doesn't know how to open it.

Give it exe-permissions:
1. Right-click the file and choose Properties
2. Click on the Permissions-tab
3. Mark the "Allow executing file as program" and then close 
4. Double-click the file again


/N

---

### Post by howefield on 2009-12-28
> **dannyboy75 said:**
> If  anyone can point me in the right direction I'd really appreciate it

Open a terminal and type

```
sudo chmod a+x ueav.i386.linux
```

then type

```
./ueav.i386.linux
```

That should start the program installer. But as others have said, there are reasons for running antivirus on linux, do you have one of them ?
:lolflag:

---

### Post by dannyboy75 on 2009-12-28
thanks for the responses guys. I know it's not strictly necessary to run AV on Linux, but I was just curious to try this new Eset product as I used to work for them.  

steveneddy - yes I know it's BETA software, but my Ubuntu environment is itself only a test environment, and to help me familiarise myself with Linux a little better. Also Eset are a well established, global and reputable AV company. I take your point about the wisdom of sticking to the repositories though.

I know I don't really need to install this particular software, but it's still helpful to know the cause of the error, as I'm bound to see the same error with other apps later down the line.

WakkiTabakki - thanks for the tip, I will try this later !

cheers

---

### Post by steveneddy on 2009-12-28
I understand that they seem to be a reputable company, but the simple fact that those running AV software don't run that particular company's software and probably haven't heard of it until now 

( I am probably wrong on this )

but feel free to compare it to the clamav product that most of us use. ( I don't but many do )

The links in my sig will also help you understand Ubuntu and help you find help faster.

Let us know how that product works on Ubuntu. It may be something that the server crowd may be interested in as most of them use the server edition in a professional environment that requires anti-virus software.

---

### Post by warfacegod on 2009-12-28
Sorry to jump in.

> It may be something that the server crowd may be interested in as most of them use the server edition in a professional environment that requires anti-virus software.

Why do the servers need AV? Is it to help protect windows machines?

---

### Post by mlentink on 2009-12-28
On Windows NOD32 is far superior to ClamAV, so I can imagine someone wanting to try it out. Especially if you're running a Linux server and also serve Windows-clients (as most are). 
I'd be interested to hear about your experiences.

---

### Post by mlentink on 2009-12-28
> **warfacegod said:**
> Why do the servers need AV? Is it to help protect windows machines?


Obviously...

---

### Post by steveneddy on 2009-12-28
> **warfacegod said:**
> Sorry to jump in.



Why do the servers need AV? Is it to help protect windows machines?

Basically, yes.

You you are file sharing, file serving or operate a mail server, these applications will benefit from AV ir service to a Windows client.

Also if one has a desktop and forwards e-mail from the Ubuntu machine to friends running Windows, one can scan attachments before sending them off.

---

### Post by audiomick on 2009-12-28
> **warfacegod said:**
> 
Why do the servers need AV? Is it to help protect windows machines?

As far as I can tell, the answer to that is "mostly, but not only"

---

### Post by warfacegod on 2009-12-28
So basically linux users need Windows to keep the folks that write viruses occupied.

---

### Post by dannyboy75 on 2009-12-28
Ticking the little box to allow it to run as an executable did the trick, installation was just via a straightforward wizard then.

In the interests of learning, I also tried installing it via the command line method in **howefield's** post, which also worked fine.

The AV seems to work ok too, it blocked access to the eicar.com test file I downloaded. Main difference over the Windows version is no HTTP scanning, it's file-level only, but the overall look and feel is the same.

Bearing in mind the comments above though, I probably won't leave it installed as it seems a waste of resources, all things considered.

Thanks again for all the replies, it's brilliant to see such a well populated and enthusiastic forum. :P

---

### Post by mlentink on 2009-12-28
> **dannyboy75 said:**
> Main difference over the Windows version is no HTTP scanning, it's file-level only, but the overall look and feel is the same.

Hmm. That wouldn't be to much of a problem on a server. It would cover ftp uploads and getting it to scan incoming mail should be doable.

But I guess it wouldn't be free....

---

### Post by dannyboy75 on 2009-12-28
no, they don't do a free version.

---

### Post by Portable_Jim on 2010-01-03
Please mark this thread as solved.

Up the top of the page "Thread Tools" => "Mark this thread as solved".

---

### Post by iGThomas on 2011-06-17
> **WakkiTabakki said:**
> The problem is that when you downloaded the file, it didn't get saved with executable permissions (which is by-design)... 
The somewhat cryptic message you get means that, since it's not allowed to run the executable file, it doesn't know how to open it.

Give it exe-permissions:
1. Right-click the file and choose Properties
2. Click on the Permissions-tab
3. Mark the "Allow executing file as program" and then close 
4. Double-click the file again


/N
Thanks it worked for me )))

---

