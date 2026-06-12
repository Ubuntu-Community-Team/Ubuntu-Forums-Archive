---
title: "Equifax Certificate error between citrix and Ubuntu"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Trandre on 2010-03-20
Hi 

I've struggeled abit with connecting through my https portal citrix login from my Ununtu computer.

I have now clean my pc from all certificates etc, and try to start over again.
I have a fresh install of "Citrix Presentation Server Client for Linux x86" and followed the install.txt.
I have follow alot of threads earlier to figure the certificate issue out with no luck. I have (but now removed) installed the certificate from the vendors home page and inserted it in the right folder etc. But I couldt validate it. I have tried accesing through chrome, but it will not download the ica file. But with firefox I get to this stage:
When logging on I get the below message.  Can anyone help with this issue?


Trandre

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150795&stc=1&d=1269116891[/IMG]

---

### Post by Trandre on 2010-03-21
bump

---

### Post by Trandre on 2010-03-21
bump

---

### Post by patchwork on 2010-03-21
You have a very specific problem, and it may take awhile for someone who has experience with this to find it and answer.  Please be patient.

On the off chance that it is related, do you have NoScript installed on firefox, and if so, have you chosen to not trust your website?

---

### Post by Trandre on 2010-03-21
I havent activly not trusted any sites and if No script is an extention I havent knowingly installed that either.

This my extentions in firefox
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150914&stc=1&d=1269207808[/IMG]

And this is in norwegian the certificate reports that pop up when I open firefox extentions(it says coulndt control the certificate of unknown reasons):
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150915&stc=1&d=1269207808[/IMG]


Trandre
Trying to be a bit more patient :-)

---

### Post by Trandre on 2010-03-21
My add ons

Trandre

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150919&stc=1&d=1269208088[/IMG]

---

### Post by patchwork on 2010-03-22
What folder did you save the certificate to?  I found this thread 
[http://ubuntuforums.org/showthread.php?t=1322608](http://ubuntuforums.org/showthread.php?t=1322608) where the poster had a similar problem and solved it by saving the certificate as superuser into a specific folder.

Hope this helps.

---

### Post by Trandre on 2010-03-23
Hi tried to follow this Description:https: //help.ubuntu.com/community/CitrixICAClientHowTo
```
32-bit
Install Citrix's 32-bit client from its linux clients download page (currently here), then add any needed libraries and make them work with your system.

1. Install the 32-bit Citrix client.

Download the linux client tarball (currently here) to some temp dir, e.g. /tmp/citrix
Extract the tarball, e.g. (change parameters as necessary)

DOWNLOAD_DIR="/tmp/citrix"
TARBALL_FN="linuxx86-11.0.140395.tar.gz"
pushd ${DOWNLOAD_DIR}
tar xfz ${TARBALL_FN} # add '> /dev/null' for quiet
```

Got this result:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=151184&stc=1&d=1269375051[/IMG]

What am I doing wrong?


Trandre

---

### Post by patchwork on 2010-03-23
It says it can't find the temp directory 'citrix'.  Did you make the directory first?

```
mkdir /tmp/citrix
```

---

### Post by Trandre on 2010-03-23
Thanks Patchwork, that did the trick, Now I came this long:

```
famfem@famfem-desktop:~$ mkdir /tmp/citrix
famfem@famfem-desktop:~$ mkdir /tmp/citrix
mkdir: kan ikke opprette katalog «/tmp/citrix»: File exists
famfem@famfem-desktop:~$ ^C
famfem@famfem-desktop:~$ DOWNLOAD_DIR="/tmp/citrix"
famfem@famfem-desktop:~$ TARBALL_FN="linuxx86-11.0.140395.tar.gz"
famfem@famfem-desktop:~$ pushd ${DOWNLOAD_DIR}
/tmp/citrix ~
famfem@famfem-desktop:/tmp/citrix$ sudo ./setupwfc
sudo: ./setupwfc: command not found
famfem@famfem-desktop:/tmp/citrix$ sudo ./setupwfc
sudo: ./setupwfc: command not found
famfem@famfem-desktop:/tmp/citrix$ 

```

This is my directory:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=151189&stc=1&d=1269376166[/IMG]

Why cant it find the Command?

Trandre

---

### Post by patchwork on 2010-03-23
You need to unpack the tarball first:  This is automated in the script you're running (but the filename in the script doesn't match the filename of your tarball).  Try this
```
cd /tmp/citrix
tar xzvf linuxx86.tar.gz
sudo ./setupwfc
```

---

### Post by Trandre on 2010-03-23
Thanx again it worked PatchWork together with this Howto: [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

Now for the Certificate part :-)
I probobly will be back :-)


Trandre

---

### Post by Trandre on 2010-03-23
> **patchwork said:**
> What folder did you save the certificate to?  I found this thread 
[http://ubuntuforums.org/showthread.php?t=1322608](http://ubuntuforums.org/showthread.php?t=1322608) where the poster had a similar problem and solved it by saving the certificate as superuser into a specific folder.

Hope this helps.

OK, now I know that the install is good, but I am back to the original message of trust equifax blah blah.

I followed the post Patchwork posted and saved the correct file in that directory. But I still have the error.

The thing that I havent doneas described is sudocopy in the directory, dont know what it means. What I did was to save as from the website displayed in another post: [https://www.geotrust.com/resources/root-certificates/index.html](https://www.geotrust.com/resources/root-certificates/index.html)

Any Idea what sudo copy somthing is and howto?

Trandre

---

### Post by patchwork on 2010-03-23
The sudo prefix gives you temporary 'superuser' rights to run a command.  In this case, to copy a file into a directory.


Keep in mind I haven't done this myself, I am just trying to relate what the original poster described.  I think the poster in the other thread made a mistake in his answer...

> ./usr/lib/ICAClient/keystore

I believe it's supposed to be /usr/lib/ICAClient/keystore (without the .)
If this is where you saved the file, you should have been denied access to the directory without superuser rights.

First, ensure that you have the proper directory:
```
cd /usr/lib/ICAClient/keystore
```
then download the certificate to your Downloads folder.
Next:```
sudo cp ~/Downloads/certificatefilename /usr/lib/ICAClient/keystore
```

---

### Post by Trandre on 2010-03-23
I think your on to something because when I looked for the file it is not there. But I stooped here as seen on print screen, what have >I done wrong?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=151200&stc=1&d=1269379571[/IMG]


Trandre

---

### Post by patchwork on 2010-03-23
Try this:

```
sudo cp /home/famfem/Downloads/Equifax_Secure_Certificate_Authority.cer /usr/lib/ICAClient/keystore/
```

EDIT:  I hope the x server warnings are from something else you're working on?

---

### Post by Trandre on 2010-03-23
This is my download deposit:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=151201&stc=1&d=1269379822[/IMG]

---

### Post by Trandre on 2010-03-23
Yup thats from a get stable video stream project, I have layd it to rest for a while :-)

---

### Post by patchwork on 2010-03-23
I think the previous error you had was from using the - character before the /Downloads (/Nedlastiger) instead of ~ 

```
sudo cp ~/Nedlastinger/Equifax_Secure_Certifiacte_Authority.cer /usr/lib/ICAClient/keyword
```

---

### Post by Trandre on 2010-03-23
Thank you, yes. I finally got into the directory, thanks to you. But it still will not work.

I read a new post that stated that I should rename it to .cert instead of .cer

How is this done, when the file is locked for editing?

Probobly gksudo  "something" /usr/lib/ICAClient/keystore//Equifax_Secure_Certificate_Authority.cer

Trandre

---

### Post by patchwork on 2010-03-23
```
sudo cp /usr/lib/ICAClient/keyword/Equifax_Secure_Authority.cer /usr/lib/ICAClient/keyword/Equifax_Secure_Authority.cert
```

---

### Post by Trandre on 2010-03-23
Thanks a lot for your help, Patchwork.

I learned a lot about CLI, but didn't manage to log on to work. I have take the battle up later on, bedtime for me.

But now I have a correct .crt and .cer file in the correct directory, so I'm closer.

But still have the first error message that I dont trust Equifax...

Good night


Trandre

---

### Post by patchwork on 2010-03-23
From [here]("http://citrix.utipu.com/app/tip/id/7731/"), the file needs to be one directory deeper.

```
sudo cp /usr/lib/ICAClient/keystore/Equifax_Secure_Authority.cer //usr/lib/ICAClient/keystore/cacerts/Equifax_Secure_Authority.crt
```

---

### Post by Trandre on 2010-03-25
Thanx Patchwork. 

I did that, but it still didn't work. But later I found another repository with crt contents as in the  mentioned folder exept the Equifax. That was in home/something/ICAClient/keystore/cacerts.

So I used your method for cp over in that container. 

And now I got the weiredst Error Message. I think my machine suffers from Scizophrenia :-)

Trandre

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=151398&stc=1&d=1269512963[/IMG]

---

### Post by Trandre on 2010-03-25
And now this one

Trandre
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=151399&stc=1&d=1269513199[/IMG]

---

### Post by patchwork on 2010-03-25
From the [citrix forum]("http://forums.citrix.com/thread.jspa?threadID=90997&tstart=0"), other users experiencing problems similar to your second problem (corrupt ica file) have been able to resolve the issue by clearing cookies, clearing temp files, and disabling any pop-up blocker.   

Several people responded the the original post claiming these methods worked for them as well.

---

### Post by Trandre on 2010-03-25
Thanx Patchwork

Now I need to run this script, but i dont understand how. I am really a newbie and thanx for your patience.

Trandre

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=151401&stc=1&d=1269518763[/IMG]

---

### Post by Trandre on 2010-03-25
Did it I think with sudo bash.


Trandre

---

### Post by patchwork on 2010-03-25
To execute a script in the current directory, you can do it by using ./scriptname

---

### Post by Trandre on 2010-03-27
Thanx that work. I had to put gksudo in front of it. 

Now I read in a post that I have to roll back my citrix to version 9. 

How can I do that?

Trandre

---

### Post by patchwork on 2010-03-27
I don't know about rolling the version back, but it may not be necessary.  I'd give the following instructions a try first.  It seems that the location for the certificates has changed in 9.10 (after you had so much trouble putting them there!).  His instructions link the old location to the new location.  If this doesn't work, you can always try to roll back the client software afterwards.


> 
From
[http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex](http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex)
_**UPDATE 09/02/2010**_:
If you have mozilla installed on your system, then you already have all the CA certs you need.
 The trick is to tell ICA Client where they are. It looks for the certs in:
/usr/lib/ICAClient/keystore/cacert
 On my Ubuntu 9.10 system, the mozilla certs are in:
/usr/share/ca-certificates/mozilla/
 My quick solution (making a backup of whatever you change first) was to simply point the ICA certs dir at the mozilla one and my citrix client started working immediately:
 mv /usr/lib/ICAClient/keystore/cacert /usr/lib/ICAClient/keystore/cacert_old
cp /usr/lib/ICAClient/keystore/cacert_old/* /usr/share/ca-certificates/mozilla/
ln -s /usr/share/ca-certificates/mozilla /usr/lib/ICAClient/keystore/cacert


---

