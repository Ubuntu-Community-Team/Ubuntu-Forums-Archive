---
title: "Citrix .ICA file opens in gedit?"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by Trandre on 2010-12-07
Hi 
I am clicking on the downloaded .ICA for my workplaces remote dektop after logging into citrix webinterface. This action just opens the .ica file in Gedit and does not open the desktop as it does in windows based system. using Chromium.

What do I need to do?
Citrix client is installed on computer.

---

### Post by Trandre on 2010-12-07
When i rightclick the Ica file and chosse open with another program citrix is not listed. Allthough i have under applications and internet.
 On the other hand when I choose citrix reciever from the app --> internet  nothing happends 

I have a 64 bit system, if that is relevant

On trying to install a new client with .deb and gdebi it says wrong arcitecture I386
Trying to use Kpackagekit it gives the following output and promt to report as a bug:


Error Type: 
Error Value: 'DebPackage' object has no attribute '_failureString'
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2216, in 
main()
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2213, in main
run(args, options.single)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2175, in run
backend.dispatcher(args)
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 699, in dispatcher
self.dispatch_command(args[0], args[1:])
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 678, in dispatch_command
self.simulate_install_files(files_to_inst)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1474, in simulate_install_files
self.error(ERROR_LOCAL_INSTALL_FAILED, deb._failureString)

---

### Post by nirlep.sanghvi@gmail.com on 2010-12-07
Trandre

Try this link, [http://ubuntuforums.org/showthread.php?t=1636973](http://ubuntuforums.org/showthread.php?t=1636973)

it works for me with Ubuntu 10.10. citrix installs fine but than my company uses juniper and I can not install Juniper.

see if this works for you and let me know if you have the same issue with Juniper.




> **Trandre said:**
> When i rightclick the Ica file and chosse open with another program citrix is not listed. Allthough i have under applications and internet.
 On the other hand when I choose citrix reciever from the app --> internet  nothing happends 

 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177747&stc=1&d=1291753707[/IMG]

---

### Post by Trandre on 2010-12-07
Thanks nirlep.sanghvi I followed the linked but got additional problems wich I updated in the former post. We probably wrote at the same time. I thought I had installed Citrix earlier but apparently i only have the Icon. Hmm Im a bit pusseled and dont know if this is related to me having a 64 based machine

---

### Post by nirlep.sanghvi@gmail.com on 2010-12-07
Does your work system use Juniper to establish a secure server link ?

> **Trandre said:**
> Thanks nirlep.sanghvi I followed the linked but got additional problems wich I updated in the former post. We probably wrote at the same time. I thought I had installed Citrix earlier but apparently i only have the Icon. Hmm Im a bit pusseled and dont know if this is related to me having a 64 based machine

---

### Post by Trandre on 2011-01-07
I dont know if it runs juniper. But this is how i log in. Go to [https://so](https://so) on.. website. Enter credentials, password and a passcode from my RSA SucurID badge. Then I am in a citrix pre environment, I choose desktop and a .ica file downloads. When i press the .ica file I go in to gedit and not citrix.

---

### Post by Trandre on 2011-01-12
bump

---

