---
title: "Pam Face Authentication Problem"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by Intzi1992 on 2011-08-30
I want to install to my computer a face recognition lock system and i found the Pam Face. So I go to **[http://pam-face-authentication.org/downloads.php](http://pam-face-authentication.org/downloads.php)** The site of the program i follow the instructions and when i write to the terminal the 3d command ( 									**sudo apt-get install pam-face-authentication** ) It give me this message.

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 pam-face-authentication : Depends: libcv2.1 but it is not going to be installed
                           Depends: libcvaux2.1 but it is not going to be installed
                           Depends: libhighgui2.1 but it is not going to be installed
E: Broken packages
[/I]
Does anyone know what do i have to do to fix it?  **ThX! :D**

---

### Post by Enigmapond on 2011-08-30
Do yourself a great service and do not install this face recognition software. Be thankful it didn't install. I had serious issues with it that got so bad, I had to to a fresh install. No one here could provide any assistance during my crisis...you can obviously do what you like, but I urge you to  re-think this. It's far from being perfected and if it did not work right in Lucid, I very much doubt it will work in anything later.

Good Luck! Back up  your data... :)

---

### Post by jtarin on 2011-08-30
> **Intzi1992 said:**
> I want to install to my computer a face recognition lock system and i found the Pam Face. So I go to **[http://pam-face-authentication.org/downloads.php](http://pam-face-authentication.org/downloads.php)** The site of the program i follow the instructions and when i write to the terminal the 3d command ( 									**sudo apt-get install pam-face-authentication** ) It give me this message.

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 pam-face-authentication : Depends: libcv2.1 but it is not going to be installed
                           Depends: libcvaux2.1 but it is not going to be installed
                           Depends: libhighgui2.1 but it is not going to be installed
E: Broken packages
[/I]
Does anyone know what do i have to do to fix it?  **ThX! :D**[Try this]("http://www.mydigitallife.info/ubuntu-unmet-dependencies-not-going-to-be-installed-or-try-apt-get-f-install-error/")....but [U]heed the warning from the poster above.
[/U]

---

