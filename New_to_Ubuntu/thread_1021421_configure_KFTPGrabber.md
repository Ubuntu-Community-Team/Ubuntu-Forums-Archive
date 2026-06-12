---
title: "configure KFTPGrabber?"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by stickman51 on 2008-12-25
Got Ubuntu 8.10 a week ago. SLOWLY learning. In Windoze, I use WS_FTP LE and it is VERY nice. For Ubuntu I got Filezilla but found it poor, so got KFTPGrabber. But I can't see any instructions for it and see only two "Local Session" windows, and no arrows between them. Under "Help" if I try "KFTPGrabber Handbook" I get an error message: "Could not launch the KDE Help Center; could not find service 'khelpcenter.'"
Can somebody please help out this old geezer here?

---

### Post by ken22 on 2008-12-25
Hi,

```
sudo apt-get install khelpcenter 
```

should do it.

[Here]("http://taufanlubis.wordpress.com/2008/05/02/khelpcenter-%E2%80%93-kde-help-center/") for details.

---

### Post by stickman51 on 2008-12-25
thanks for that, Ken22; I did that "Terminal" thingy and it took a half hour or so to do its thing. I rebooted, restarted KFTPGrabber, tried the Help again but get the same error message as before. No other dialog boxes came up at all in the process but it did go thru the whole process.

---

### Post by pdtpatrick on 2008-12-25
Hmm you could try using gFTP ... however i can tell you Filezilla is very good and you can use a lot of different protocols on it ..SSH, FTP ... you might actually have a better luck with that and have lots of readme on it.

---

### Post by stickman51 on 2008-12-25
Thanks, Patrick; a screenshot of KFTPG. looked fairly similar to WS_FTP so I figured it would be good. I found Filezilla awkward by comparison to WS. Maybe if I can get this HELP thingy to work I can make KFTP. work.

---

### Post by pdtpatrick on 2008-12-25
run this:

sudo apt-cache search khelpcenter4
see if thats there.. if it is then run

sudo apt-get install khelpcenter4

once that is done .. try running sudo apt-get update and see if there are any pending updates.. if so update and then log off and back on .. now try doing what you were trying to do again.

---

### Post by stickman51 on 2008-12-25
hmmmm; we keep trying..............   ;-) Did that and here are the two printouts I got:


kenlaninga@ubuntu:~$ sudo apt-cache search khelpcenter4
[sudo] password for kenlaninga: 
khelpcenter4 - Help Center for KDE 4
kenlaninga@ubuntu:~$ run
bash: run: command not found
kenlaninga@ubuntu:~$ sudo apt-get install khelpcenter4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
khelpcenter4 is already the newest version.
khelpcenter4 set to manually installed.
The following packages were automatically installed and are no longer
required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kenlaninga@ubuntu:~$ 


and then:

kenlaninga@ubuntu:~$ sudo apt-get update
[sudo] password for kenlaninga: 
Get:1 [http://apt.wicd.net](http://apt.wicd.net) intrepid Release.gpg [197B]
Ign [http://apt.wicd.net](http://apt.wicd.net) intrepid/extras
Translation-en_CA                      
Get:2 [http://apt.wicd.net](http://apt.wicd.net) intrepid Release
[8847B]                             
Ign [http://apt.wicd.net](http://apt.wicd.net) intrepid
Release                                       
Ign [http://apt.wicd.net](http://apt.wicd.net) intrepid/extras
Packages                               
Hit [http://apt.wicd.net](http://apt.wicd.net) intrepid/extras Packages         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release.gpg    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Translation-en_CA
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Translation-en_CA
[3750B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release.gpg
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main
Translation-en_CA [2731B]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted
Translation-en_CA [3750B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe
Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse
Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid Release      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/multiverse Sources
Fetched 10.4kB in 4s (2163B/s)
Reading package lists... Done
W: GPG error: [http://apt.wicd.net](http://apt.wicd.net) intrepid Release: The following
signatures couldn't be verified because the public key is not available:
NO_PUBKEY FEC820F4B8C0755A
W: You may want to run apt-get update to correct these problems
kenlaninga@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13
Permission denied)
E: Unable to lock the list directory
kenlaninga@ubuntu:~$ 


and still the help does not come up.    ;-(

---

### Post by pdtpatrick on 2008-12-25
so it installed fine and how are you trying to run it or use it?

---

### Post by pdtpatrick on 2008-12-25
go here.. 
[http://taufanlubis.wordpress.com/2008/05/02/khelpcenter-%E2%80%93-kde-help-center/](http://taufanlubis.wordpress.com/2008/05/02/khelpcenter-%E2%80%93-kde-help-center/)

---

### Post by ken22 on 2008-12-25
> **pdtpatrick said:**
> go here.. 
[http://taufanlubis.wordpress.com/2008/05/02/khelpcenter-%E2%80%93-kde-help-center/](http://taufanlubis.wordpress.com/2008/05/02/khelpcenter-%E2%80%93-kde-help-center/)

Unfortunately, I already suggested that in my original post.

I notice his sudo apt-get update finished with errors. Perhaps he had another package manager running at the time, such as synaptic.

---

### Post by pdtpatrick on 2008-12-25
are you talking about this?
W: GPG error: [http://apt.wicd.net](http://apt.wicd.net) intrepid Release: The following
signatures couldn't be verified because the public key is not available:
NO_PUBKEY FEC820F4B8C0755A
W: You may want to run apt-get update to correct these problems
kenlaninga@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13
Permission denied)
E: Unable to lock the list directory

looks like he adviced to run apt-get update but instead of running sudo apt-get update .. he ran apt-get update. So he didnt have enough rights to run it thats why he got that message.

Also seems his wicd package might be corrupt so he needs to reinstall most likely.

---

### Post by stickman51 on 2008-12-25
Yes, I saw those comments re errors. I've been into Ubuntu for a week or so, and don't have a clue as to where to go from here. Am I just plain out of luck?

---

### Post by albinootje on 2008-12-25
> **stickman51 said:**
> Got Ubuntu 8.10 a week ago. SLOWLY learning. In Windoze, I use WS_FTP LE and it is VERY nice. For Ubuntu I got Filezilla but found it poor, so got KFTPGrabber. But I can't see any instructions for it and see only two "Local Session" windows, and no arrows between them. 

You want a ftp-client with arrows ? 
Try gftp.
```

sudo apt-get install gftp

```
And about your apt-get error message. Try closing down "add/remove" and or "Synaptic package manager" first. 
Then try again.

And thanks for your interesting personal message.

A happy x-mas from Linus
[http://ubuntuforums.org/showthread.php?t=1021423](http://ubuntuforums.org/showthread.php?t=1021423)
:)

---

### Post by stickman51 on 2008-12-25
Thanks once again, Albinootje; THAT certainly looks like a good one; got it running and will configure it next. Looks a lot like WS_FTP LE which is VERY good in Windows.

I see YOU have a lot of "thanks" listed; 88 or something; will this add one more, automatically, or do I have to go someplace else to post an official THANKS to you?

---

### Post by albinootje on 2008-12-25
> **stickman51 said:**
> Thanks once again, Albinootje; THAT certainly looks like a good one; got it running and will configure it next. Looks a lot like WS_FTP LE which is VERY good in Windows.

Excellent, I hope you like it.
And if you find it too difficult to handle, or if it annoys you, then I'm convinced that Wine inside Linux can handle such a rather simple application as WS_FTP well.
> 
I see YOU have a lot of "thanks" listed; 88 or something; will this add one more, automatically, or do I have to go someplace else to post an official THANKS to you?

You're welcome, perhaps I talk too much, and I'm afraid I don't know the answer to that, hehe :)

---

### Post by stickman51 on 2008-12-25
Yup; it works fine now. Another new word: WINE; I figured that was something one drank on special occasions. hmmmmmmmmmaybe not.....

---

### Post by pdtpatrick on 2008-12-25
lol didnt i mention gftp earlier? :) just thought it was interesting.. Merry Christmas folks.

---

### Post by stickman51 on 2008-12-26
Yes, Patrick, so you DID and I thank you for it; it just did not seem all that great first try. On second try, it is much better for me. Thanks again! AND Happy New Year

---

### Post by albinootje on 2008-12-26
> **stickman51 said:**
> Yes, Patrick, so you DID and I thank you for it; it just did not seem all that great first try. On second try, it is much better for me. Thanks again! AND Happy New Year

Hi stickman51 

A super fantastic 2009 to all of you!

:)

---

