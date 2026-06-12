---
title: "Clamudo/Dazuko"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by sanjaypothen on 2010-04-10
What is clamudo/dazuko?

---

### Post by Georgia boy on 2010-04-10
[http://en.wikipedia.org/wiki/Dazuko](http://en.wikipedia.org/wiki/Dazuko)


Couldn't find anything in Google on Clamudo. Don't quite understand what this one does. Maybe someone else can take this and run with a better description on it and what exactly happens. 
Sorry, best I could do for you.

Tom

---

### Post by sanjaypothen on 2010-04-10
Well i still didn't understand, can sombody help?

---

### Post by sanjaypothen on 2010-04-11
pl.any body in the forum do you know what this is all about? I have been waiting for the past 10 hours for an answer.

---

### Post by sanjaypothen on 2010-04-12
sombody pl.help about this matter!!!!!!!???????

---

### Post by Ampi on 2010-04-12
I also have no idea, maybe this page can help??

[http://dazuko.dnsalias.org/wiki/index.php/Main_Page](http://dazuko.dnsalias.org/wiki/index.php/Main_Page)

---

### Post by Mykk on 2010-04-12
> **sanjaypothen said:**
> sombody pl.help about this matter!!!!!!!???????

Some one is going to get in trouble for ignoring the bump rule :)

---

### Post by sanjaypothen on 2010-04-12
> **Ampi said:**
> I also have no idea, maybe this page can help??

[http://dazuko.dnsalias.org/wiki/index.php/Main_Page](http://dazuko.dnsalias.org/wiki/index.php/Main_Page)
Is clamudo same as dazuko? Are they working in  my system, i have clamav.

---

### Post by Steven_S on 2010-04-12
[http://dazuko.dnsalias.org/wiki/index.php/Main_Page](http://dazuko.dnsalias.org/wiki/index.php/Main_Page)

Are you sure you didn't mean "Clamodo"? [http://nixforums.org/about20587-announcing-clamodo-spamodo-simple-clamav-SA-integration-t.html](http://nixforums.org/about20587-announcing-clamodo-spamodo-simple-clamav-SA-integration-t.html)

I know nothing of these things, but I have always found "The Google" a wonderful service to use :popcorn:.

---

### Post by sanjaypothen on 2010-04-12
NO. It is clamudo. nobody knows about it? In google there is no clamudo.

---

### Post by Sir Jasper on 2010-04-12
Hi,

Exactly how did you find it and what is the connection with any African language?

My regards

---

### Post by sanjaypothen on 2010-04-12
> **Sir Jasper said:**
> Hi,

Exactly how did you find it and what is the connection with any African language?

My regards
It is there in ubuntu 9.10.Can u help? since its name is similar to ubuntu i assumed it  to be some African language(though  i am not sure about it).

---

### Post by Sir Jasper on 2010-04-12
Hi again,

I cannot find it. Please post a screenshot.

My regards

---

### Post by e4uforums on 2010-04-12
> **sanjaypothen said:**
> NO. It is clamudo. nobody knows about it? In google there is no clamudo.

If Google doesn't know about it, it doesn't exist.  :P

---

### Post by sanjaypothen on 2010-04-13
> **Sir Jasper said:**
> Hi again,

I cannot find it. Please post a screenshot.

My regards
I have taken the screenshot,but how to post it?

---

### Post by Steven_S on 2010-04-13
When you compose a reply, you can attach the file to it. Look for the paperclip icon in the bar on top of where you type your reply...

---

### Post by sanjaypothen on 2010-04-13
> **sanjaypothen said:**
> It is there in ubuntu 9.10.Can u help? since its name is similar to ubuntu i assumed it  to be some African language(though  i am not sure about it).

> **Steven_S said:**
> When you compose a reply, you can attach the file to it. Look for the paperclip icon in the bar on top of where you type your reply...

When i upload the file,i message comes saying that the file is invalied; now how should i up load?Pl.help

---

### Post by Steven_S on 2010-04-14
Ok... what format (type of file) is the screenshot you have made? And how big is it? As you can see from the instructions when you try to attach something, you can only upload a limited image size and file size:

If you don't know how to resize the image to fit the restrictions, try to upload to it to a third party site such as photobucket.com, and posting the link here...

---

### Post by sanjaypothen on 2010-04-14
> **Steven_S said:**
> Ok... what format (type of file) is the screenshot you have made? And how big is it? As you can see from the instructions when you try to attach something, you can only upload a limited image size and file size:

If you don't know how to resize the image to fit the restrictions, try to upload to it to a third party site such as photobucket.com, and posting the link here...

Ok. Here is the screenshot.

---

### Post by lisati on 2010-04-14
Oh. Here we were looking for Clamudo, and it's clamuko, part of the Clam AV package.

See here: [http://www.clamav.net/doc/latest/html/node30.html](http://www.clamav.net/doc/latest/html/node30.html)

---

### Post by Steven_S on 2010-04-14
Ok, thanks! I found this: 

<quote>
**Clamuko **

     Clamuko is a special thread in clamd that performs on-access     scanning under Linux and FreeBSD and shares internal virus database     with the daemon. You must follow some important rules when     using it:      
[LIST]
[*]Always stop the daemon cleanly - using the SHUTDOWN command or           the 
SIGTERM signal. In other case you can lose access           to protected files until the system is restarted.
[*]Never protect the directory your mail-scanner software           uses for attachment unpacking. Access to all infected           files will be automatically blocked and the scanner (including           clamd!) will not be able to detect any viruses. In the           result all infected mails may be delivered.
[/LIST]
     For example, to protect the whole system add the following lines to     clamd.conf:         ClamukoScanOnAccess
    ClamukoIncludePath /
    ClamukoExcludePath /proc
    ClamukoExcludePath /temporary/dir/of/your/mail/scanning/software
    You can also use clamuko to protect files on Samba/Netatalk but a far     more better and safe idea is to use the samba-vscan module.     NFS is not supported because Dazuko doesn't intercept NFS access calls. 
 
</quote>

But... this is on the **archived** version of the page [http://www.clamav.net/doc/latest/html/node28.html](http://www.clamav.net/doc/latest/html/node28.html). On the new version, it seems to have moved. In other words: don't rely on the link provided by the previous poster to work forever 8).

There is also this old thread: [http://ubuntuforums.org/showthread.php?t=52385](http://ubuntuforums.org/showthread.php?t=52385) - might still be of use to you (way over my head).

---

### Post by sanjaypothen on 2010-04-14
> **Steven_S said:**
> Ok, thanks! I found this: 

<quote>
**Clamuko **

     Clamuko is a special thread in clamd that performs on-access     scanning under Linux and FreeBSD and shares internal virus database     with the daemon. You must follow some important rules when     using it:      
[LIST]
[*]Always stop the daemon cleanly - using the SHUTDOWN command or           the 
SIGTERM signal. In other case you can lose access           to protected files until the system is restarted.
[*]Never protect the directory your mail-scanner software           uses for attachment unpacking. Access to all infected           files will be automatically blocked and the scanner (including           clamd!) will not be able to detect any viruses. In the           result all infected mails may be delivered.
[/LIST]
     For example, to protect the whole system add the following lines to     clamd.conf:         ClamukoScanOnAccess
    ClamukoIncludePath /
    ClamukoExcludePath /proc
    ClamukoExcludePath /temporary/dir/of/your/mail/scanning/software
    You can also use clamuko to protect files on Samba/Netatalk but a far     more better and safe idea is to use the samba-vscan module.     NFS is not supported because Dazuko doesn't intercept NFS access calls. 
 
</quote>

But... this is on the **archived** version of the page [http://www.clamav.net/doc/latest/html/node28.html](http://www.clamav.net/doc/latest/html/node28.html). On the new version, it seems to have moved. In other words: don't rely on the link provided by the previous poster to work forever 8).

There is also this old thread: [http://ubuntuforums.org/showthread.php?t=52385](http://ubuntuforums.org/showthread.php?t=52385) - might still be of use to you (way over my head).


I have installed the calm-daemon and its dependencies from the synaptic package manager.The calm daemon status states as running. But i want to know if the calmdaemon is 
doining on-access scanning in my system.(2) Am i to do or start the calmdaemon(3)Is my calmdaemon testable(4)Is the calmdaemon configured and installed properly

---

### Post by Steven_S on 2010-04-14
A calm daemon is a serene evil spirit. 

(sorry, couldn't resist that 8-))

Serious now - you might try the contacts offered on the website of the application ([www.clamav.net](www.clamav.net)). I'm sure they will be able to direct you to more detailed information.

---

