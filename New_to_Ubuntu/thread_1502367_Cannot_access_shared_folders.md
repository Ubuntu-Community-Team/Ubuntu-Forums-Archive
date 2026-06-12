---
title: "Cannot access shared folders"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by ubantunovice on 2010-06-05
I am using Oracle Virtualbox 3.2.0 installed in Windows 7 home premium 64 bit. I successfully installed 2 virtual OSs, XP and Ubuntu 10.04.

This question deals with accessing host files from within Ubuntu. (I succeeded in doing so in Windows XP but cannot in Ubuntu perhaps because I am using the wrong command to mount it.)

In both cases I used virtualbox 's Device\Shared folders to add 2 folders to the virtual os.  This part was identical in both OSs.
See attachment ubuntu.gif

Then I opened a terminal in Ubuntu and entered the command
    sudo mount -t vboxsf share ~/host
and got the errors in attachment ubuntu2.gif

Searching for possible causes in the web I found the following answer: 
'You mount the SF on a mount point with the same name as the share itself, change the name or mount point'.

Don't know what to do different or even if this is the correct command to mount shared folders in Ubunto.

Any advice and help appreciated.

---

### Post by NUboon2Age on 2010-06-05
Does the info in this link help?
[http://www.giannistsakiris.com/index.php/2008/04/09/virtualbox-access-windows-host-shared-folders-from-ubuntu-guest/](http://www.giannistsakiris.com/index.php/2008/04/09/virtualbox-access-windows-host-shared-folders-from-ubuntu-guest/)

---

### Post by ubantunovice on 2010-06-05
Thank you NUboon2Age.  I will try it.
Thanks.

---

### Post by NUboon2Age on 2010-06-05
Here's my google search that found that link:

[http://www.google.com/search?hl=en&client=firefox-a&rls=Swiftfox%3Aen-US%3Aunofficial&q=mount+shared+folder+virtualbox+ubuntu&aq=0c&aqi=g-c2&aql=&oq=mount+shared+ubuntu&gs_rfai=](http://www.google.com/search?hl=en&client=firefox-a&rls=Swiftfox%3Aen-US%3Aunofficial&q=mount+shared+folder+virtualbox+ubuntu&aq=0c&aqi=g-c2&aql=&oq=mount+shared+ubuntu&gs_rfai=)

---

### Post by ubantunovice on 2010-06-05
> **NUboon2Age said:**
> Does the info in this link help?
[http://www.giannistsakiris.com/index.php/2008/04/09/virtualbox-access-windows-host-shared-folders-from-ubuntu-guest/](http://www.giannistsakiris.com/index.php/2008/04/09/virtualbox-access-windows-host-shared-folders-from-ubuntu-guest/)

Did not work either.  See attached image.
It is not a permission problem in W 7 because the same file mounted fine in the virtual XP. I'm just doing something wrong and don't know what it is.

---

### Post by mws604 on 2010-06-12
I am trying the same thing and getting a different type of error:


 sudo mount -t vboxsf share ~/host
/sbin/mount.vboxsf: mounting failed with the error: Protocol error
mike-vbox@mike-vbox-desktop:~$

---

### Post by mws604 on 2010-06-12
Figured out my problem.  The syntax was incorrect.  It worked when I created a directory named 'host' under home and then entered the following command:

sudo mount -t vboxsf VBoxShare ~/host

where vboxsf is the type
      VBoxShare is the the shared folder I created on the guest vm

This statement worked and now I am sharing between my guest ubuntu and my Win7 64bit host.

Thank you NUboon2Age.

---

### Post by ubantunovice on 2010-06-13
I'm the original OP.

Glad you got it working and thanks for posting your result.  I will try that too and see if it will work for me too.

But, for someone trying to learn Linux, it is annoying to have to go through all this steps, when in the virtual XP I created it just took a simple mount command to achieve the same result. (See my original OP question). No need to create a mount point, give it a type, etc. IMHO, ideally, issuing a mount command should automatically create the necessary mount point and whatever else is needed just as it does in the virtual XP.

---

