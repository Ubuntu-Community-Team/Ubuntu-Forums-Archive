---
title: "How to install a deb.tar.gz ?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by L Campbell on 2010-02-14
I am running 8.10 on my PC and have downloaded Open Office 3.2.0 to my Desktop.

Do I 'open with Archive Manager' to install this?

TIA.

---

### Post by rcayea on 2010-02-14
This is the link you want:

[http://ubuntuforums.org/showthread.php?p=8812741](http://ubuntuforums.org/showthread.php?p=8812741)

---

### Post by ibuclaw on 2010-02-14
**deb**.tar.gz ?

Seems alot like overkill on compress. ;)


Yeah, I presume you just double click, extract the .deb, then double click on the .deb to install.

Regards
Iain

---

### Post by L Campbell on 2010-02-14
> **rcayea said:**
> This is the link you want:

[http://ubuntuforums.org/showthread.php?p=8812741](http://ubuntuforums.org/showthread.php?p=8812741)

Thanks, that looks like a great link.

I entered the first command into Terminal and it returned 'command not found', so I changed directory to Desktop and tried again, but got the same result.:-

qwer@qwer-desktop:~$ OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz
bash: OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz: command not found
qwer@qwer-desktop:~$ cd Desktop
qwer@qwer-desktop:~/Desktop$ OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz
bash: OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz: command not found
qwer@qwer-desktop:~/Desktop$

Please, what am I doing wrong here?

---

### Post by oldos2er on 2010-02-14
You need to decompress the archive first: ```
tar zxvf OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz
```

It would be better for you to install OpenOffice from a repository though. See [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by ajgreeny on 2010-02-14
If the tar.gz is like previous ones from OOo direct, you can just open the archive with archive manager by double clicking on it.  That will show one folder with three subfolders, **DEBS**, **licenses**, **readmes** and an **update** file.  The DEBS folder will contain another subfolder called desktop-integration.  Again if like previous versions, you can install the new OpenOffice alongside your current version, but will not be able to automatically add menu items; we'll come to that later.  Extract the tar.gz to a folder in home.

In a terminal navigate to the DEBS folder within that home folder with ```
cd /path/to/folder
``` and check you are there with ```
ls
``` to see all the .deb files.  Now use the command ```
sudo dpkg -i *.deb
```and all those .deb files will be installed, and any dependencies needed will be downloaded and installed as well.

If you keep your old OOo version, don't install the desktop-integration .deb file or you will give the system a big headache. That .deb would add menu items if you had removed the previous OOo version, but otherwise you will need to find all the executables for the new version; they were in /opt in previous downloads, so I assume the same will still be true, and simply make launchers to them, either in the main menu, or on your desktop.

Good luck, and I hope this helps you understand how to do such things a bit better, but as olsos2er says, you can add a ppa repo to do it the easy way, I just thought you might find this info useful for future use.

---

### Post by L Campbell on 2010-02-15
> **ajgreeny said:**
> If the tar.gz is like previous ones from OOo direct, you can just open the archive with archive manager by double clicking on it.  That will show one folder with three subfolders, **DEBS**, **licenses**, **readmes** and an **update** file.  The DEBS folder will contain another subfolder called desktop-integration.  Again if like previous versions, you can install the new OpenOffice alongside your current version, but will not be able to automatically add menu items; we'll come to that later.  Extract the tar.gz to a folder in home.

In a terminal navigate to the DEBS folder within that home folder with ```
cd /path/to/folder
``` and check you are there with ```
ls
``` to see all the .deb files.  Now use the command ```
sudo dpkg -i *.deb
```and all those .deb files will be installed, and any dependencies needed will be downloaded and installed as well.

If you keep your old OOo version, don't install the desktop-integration .deb file or you will give the system a big headache. That .deb would add menu items if you had removed the previous OOo version, but otherwise you will need to find all the executables for the new version; they were in /opt in previous downloads, so I assume the same will still be true, and simply make launchers to them, either in the main menu, or on your desktop.

Good luck, and I hope this helps you understand how to do such things a bit better, but as olsos2er says, you can add a ppa repo to do it the easy way, I just thought you might find this info useful for future use.

Thanks for your suggestions here.

This is the file that I have on my Desktop:-

OOo_3.2.0_Linuxlntel_install_wJRE_en-US_deb.tar.gz

I have tried double clicking it, right clicking and trying to open with Archive Manager, 'Extract Here' and each time I get "An error occurred while loading the archive", so I am still confused.

Could the file have become corrupted during the download process?

Kind regards.

---

### Post by coolbrook on 2010-02-15
Try downloading it again.  It should be around 175 megs.

---

### Post by Zoot7 on 2010-02-15
> **L Campbell said:**
> Thanks for your suggestions here.

This is the file that I have on my Desktop:-

OOo_3.2.0_Linuxlntel_install_wJRE_en-US_deb.tar.gz

I have tried double clicking it, right clicking and trying to open with Archive Manager, 'Extract Here' and each time I get "An error occurred while loading the archive", so I am still confused.

Could the file have become corrupted during the download process?

Kind regards.
Try extracting it with 
```
tar xvf OOo_3.2.0_Linuxlntel_install_wJRE_en-US_deb.tar.gz
```

---

### Post by L Campbell on 2010-02-15
> **Zoot7 said:**
> Try extracting it with 
```
tar xvf OOo_3.2.0_Linuxlntel_install_wJRE_en-US_deb.tar.gz
```

Thank you.  I tried this but didn't have any luck.

qwer@qwer-desktop:~$ tar xvf OOo_3.2.0_Linuxlntel_install_wJRE_en-US_deb.tar.gz
tar: OOo_3.2.0_Linuxlntel_install_wJRE_en-US_deb.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


qwer@qwer-desktop:~$ cd Desktop tar xvf OOo_3.2.0_Linuxlntel_install_wJRE_en-US_deb.tar.gz
qwer@qwer-desktop:~/Desktop$ 

Kind regards.

---

### Post by Satoru-san on 2010-02-15
cd to your desktop, then Type the first letter capital O and hit <tab> <tab> this will show you the completions, if it doesnt auto complete type the next letter.

tar xvzf O <tab> <tab>

---

### Post by L Campbell on 2010-02-15
> **coolbrook said:**
> Try downloading it again.  It should be around 175 megs.

OK, thanks, it is 34 megs now.

I read that the 'w' before the JRE is to indicate 'without' JRE .

Could that account for the missing 141 megs?

Kind regards.

---

### Post by tom.swartz07 on 2010-02-15
> **L Campbell said:**
> Thank you.  I tried this but didn't have any luck.

qwer@qwer-desktop:~$ tar xvf OOo_3.2.0_Linuxlntel_install_wJRE_en-US_deb.tar.gz
tar: OOo_3.2.0_Linuxlntel_install_wJRE_en-US_deb.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


qwer@qwer-desktop:~$ cd Desktop tar xvf OOo_3.2.0_Linuxlntel_install_wJRE_en-US_deb.tar.gz
qwer@qwer-desktop:~/Desktop$ 

Kind regards.

Hiya!

I cant verify this for certain, but I know that today the official repository for OpenOffice was to update to version 3.2

You could easily upgrade the old version of OO on your system by
SYSTEM>ADMINISTRATION>SOFTWARE SOURCES, click the "Other Software" Tab, click the ADD button and copy & paste this ```
[COLOR="DeepSkyBlue"]ppa:openoffice-pkgs/ppa[/COLOR]
``` into the dialogue.

Then run Update Manager and you should be able to UPGRADE.

If its not there, it will most certainly be there by tomorrow or Wednesday

---

### Post by L Campbell on 2010-02-15
> **Satoru-san said:**
> cd to your desktop, then Type the first letter capital O and hit <tab> <tab> this will show you the completions, if it doesnt auto complete type the next letter.

tar xvzf O <tab> <tab>

Thanks, I tried this and here is what I got:-

qwer@qwer-desktop:~$ cd Desktop
qwer@qwer-desktop:~/Desktop$ tar xvzf OOo_3.2.0_LinuxIntel_install_wJRE_en-US_deb.tar.gz OOO320_m12_native_packed-1_en-US.9483/

Kind regards.

---

### Post by L Campbell on 2010-02-15
> **tom.swartz07 said:**
> Hiya!

I cant verify this for certain, but I know that today the official repository for OpenOffice was to update to version 3.2

You could easily upgrade the old version of OO on your system by
SYSTEM>ADMINISTRATION>SOFTWARE SOURCES, click the "Other Software" Tab, click the ADD button and copy & paste this ```
[COLOR="DeepSkyBlue"]ppa:openoffice-pkgs/ppa[/COLOR]
``` into the dialogue.

Then run Update Manager and you should be able to UPGRADE.

If its not there, it will most certainly be there by tomorrow or Wednesday

Hi, I appreciate your suggestion here.  The way my luck has been going, I think I'll wait till the morning to try it.    :-)

Kind regards.

---

### Post by tom.swartz07 on 2010-02-15
> **L Campbell said:**
> Hi, I appreciate your suggestion here.  The way my luck has been going, I think I'll wait till the morning to try it.    :-)

Kind regards.

Sure thing- Although it might be quicker to download and fight with the deb file, the method that I have described assures that your version of OO that is installed on the computer is up to date, and you dont have to worry about any compressed deb files. :p

I figure, its worth a shot at least, right?

---

### Post by L Campbell on 2010-02-16
> **tom.swartz07 said:**
> Sure thing- Although it might be quicker to download and fight with the deb file, the method that I have described assures that your version of OO that is installed on the computer is up to date, and you dont have to worry about any compressed deb files. :p

I figure, its worth a shot at least, right?

OK, I'm made some progress but then got stuck again.

I hope this screenshot will show where I am at:-

---

### Post by tom.swartz07 on 2010-02-16
> **L Campbell said:**
> OK, I'm made some progress but then got stuck again.

I hope this screenshot will show where I am at:-

I see you edited to fix the screenshot, but it still didnt show. Try adding it as an attachment rather than link to it in the post.

---

### Post by L Campbell on 2010-02-16
> **tom.swartz07 said:**
> Sure thing- Although it might be quicker to download and fight with the deb file, the method that I have described assures that your version of OO that is installed on the computer is up to date, and you dont have to worry about any compressed deb files. :p

I figure, its worth a shot at least, right?

OK, I'm made some progress but then got stuck again.

I hope this screenshot will show where I am at:-

**[COLOR="Red"]SCREENSHOT WILL NOT SHOW UP[/COLOR]**

---

### Post by tom.swartz07 on 2010-02-16
> **L Campbell said:**
> OK, I'm made some progress but then got stuck again.

I hope this screenshot will show where I am at:-

**[COLOR="Red"]SCREENSHOT WILL NOT SHOW UP[/COLOR]**

Create a new post. Below where you type the message, you will see a box that says manage attachments. 

Make sure you click the upload button to put the pics there. See the attachments i have for the method.

---

### Post by L Campbell on 2010-02-16
> **tom.swartz07 said:**
> Create a new post. Below where you type the message, you will see a box that says manage attachments. 

Make sure you click the upload button to put the pics there. See the attachments i have for the method.

I think I can see what I did.  I saved the screenshot as 'screenshot1' and forgot to add '.png'

---

### Post by sandyd on 2010-02-16
> **L Campbell said:**
> I think I can see what I did.  I saved the screenshot as 'screenshot1' and forgot to add '.png'
```

sudo add-apt-repository **ppa:openoffice-pkgs/ppa**
```
only works in ubuntu v.9.10

---

### Post by L Campbell on 2010-02-16
> **carlee said:**
> ```

sudo add-apt-repository **ppa:openoffice-pkgs/ppa**
```
only works in ubuntu v.9.10

OK, thanks, I'm using 8.10 so I guess I'll have to save this for later.

Kind regards.

---

### Post by sandyd on 2010-02-16
copy and paste.
dont change anything.
```

mkdir ~/OpenOfficeTMP
cd ~/OpenOfficeTMP
wget -c http://download.services.openoffice.org/files/stable/3.2.0/OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz
tar xvfz OOo*
cd OOO*
cd DEBS
cd desktop*
mv * ../
cd ../
sudo apt-get remove openoffice.org*
sudo dpkg -i *.deb

```

---

### Post by lavinog on 2010-02-16
Is there a reason why you are installing 3.2?
Why do you not upgrade to a more recent version of ubuntu (you are going to need to in april anyway.)  Why not make the transition smoother by sticking to official repositories and updating to 9.10 so when 10.04 is released you can update straight to that.

---

### Post by L Campbell on 2010-02-17
> **lavinog said:**
> Is there a reason why you are installing 3.2?
Why do you not upgrade to a more recent version of ubuntu (you are going to need to in april anyway.)  Why not make the transition smoother by sticking to official repositories and updating to 9.10 so when 10.04 is released you can update straight to that.

You make a good point here.

I recently changed from 8.04.4 to 8.10 so that I could get the Skype phone, which does not appear to be available for the other versions.

Had I seen Skype for 9.10, I would have changed to it, as I do plan to get 10.04 when it is ready.

Kind regards.

---

### Post by tom.swartz07 on 2010-02-17
> **L Campbell said:**
> You make a good point here.

I recently changed from 8.04.4 to 8.10 so that I could get the Skype phone, which does not appear to be available for the other versions.

Had I seen Skype for 9.10, I would have changed to it, as I do plan to get 10.04 when it is ready.

Kind regards.

At the expense of sounding elitist, but the Devs at Skype arent exactly the most knowledgeable when it comes to the nomenclature of the Ubuntu versions. 

When they say that Skype works for 8.10, they mean that ***the earliest version that will work*** is 8.10. I have skype on my 9.10 box and it works great!

---

### Post by L Campbell on 2010-02-17
> **carlee said:**
> copy and paste.
dont change anything.
```

mkdir ~/OpenOfficeTMP
cd ~/OpenOfficeTMP
wget -c http://download.services.openoffice.org/files/stable/3.2.0/OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz
tar xvfz OOo*
cd OOO*
cd DEBS
cd desktop*
mv * ../
sudo apt-get remove openoffice.org*
sudo dpkg -i *.deb

```

Thank you for all your efforts here.  I appreciate you sticking with me.

Everything seemed to go smoothly except for the very last line:-

ktop-integration$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
qwer@qwer-desktop:~/OpenOfficeTMP/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration$ 

Kind regards.

---

### Post by L Campbell on 2010-02-17
> **tom.swartz07 said:**
> At the expense of sounding elitist, but the Devs at Skype arent exactly the most knowledgeable when it comes to the nomenclature of the Ubuntu versions. 

When they say that Skype works for 8.10, they mean that ***the earliest version that will work*** is 8.10. I have skype on my 9.10 box and it works great!

Once again I learn something,thanks.

I thought that I had read something recently about Skype and Ubuntu getting crossways about a license, code, or something and that was why it was no longer available.

Kind regards.

---

### Post by sandyd on 2010-02-17
> **L Campbell said:**
> Thank you for all your efforts here.  I appreciate you sticking with me.

Everything seemed to go smoothly except for the very last line:-

ktop-integration$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
qwer@qwer-desktop:~/OpenOfficeTMP/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration$ 

Kind regards.

fixed typo

---

### Post by L Campbell on 2010-02-17
> **carlee said:**
> fixed typo

I'm really sorry that I'm so dense but I don't see which line you made a correction in.

I assumed it was in the last line, so I re-pasted that in again but got the same result as I had previously.  :-(

Kind regards.

---

### Post by sandyd on 2010-02-17
> **L Campbell said:**
> I'm really sorry that I'm so dense but I don't see which line you made a correction in.

I assumed it was in the last line, so I re-pasted that in again but got the same result as I had previously.  :-(

Kind regards.

I did a typo while typing ```

cd ../
```

---

### Post by L Campbell on 2010-02-18
> **carlee said:**
> fixed typo

MANY THANKS !!

That worked perfectly and I really appreciate it.

Kind regards.

---

### Post by sandyd on 2010-02-18
your welcome :)
glad I helped

---

