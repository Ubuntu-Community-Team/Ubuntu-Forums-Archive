---
title: "Can't install Plymouth themes"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by steigerjb on 2010-12-30
I can't install Plymouth themes for the life of me. It kinda worked for my ubuntu i have in virtualbox but it looks all weird. See picture.

It was the same thing for my regular ubuntu install but now the Plymouth manager wont even open. Again, see picture.

What am I doing wrong? What is the correct way to install plymouth manager, install themes, and apply them?

Thanks.

---

### Post by matt_symes on 2010-12-30
Hi

To fix plymouth at, the terminal, try

```
sudo dpkg-reconfigure gdm
```

Enter your password. You will not see it echoed to the screen. This may fix plymouth manager but i'm not sure.

Install the themes you want to try from synaptic package manager.

Once installed, open a terminal and type

```
sudo update-alternatives --config default.plymouth
```

This will give a list of the installed themes. Follow the instructions and select the theme you want. Then, in the terminal, type

```
sudo update-initramfs -u
```

This will update initramfs and, after rebooting, you should see the new theme.

This has worked for me.

Kind regards.

---

### Post by steigerjb on 2010-12-30
> **matt_symes said:**
> Hi

To fix plymouth at, the terminal, try

```
sudo dpkg-reconfigure gdm
```

Enter your password. You will not see it echoed to the screen. This may fix plymouth manager but i'm not sure.

Install the themes you want to try from synaptic package manager.

Once installed, open a terminal and type

```
sudo update-alternatives --config default.plymouth
```

This will give a list of the installed themes. Follow the instructions and select the theme you want. Then, in the terminal, type

```
sudo update-initramfs -u
```

This will update initramfs and, after rebooting, you should see the new theme.

This has worked for me.

Kind regards.

No, reconfiguring didn't fix it.

I have no boot splash what so ever right now :( Just a whole bunch of text gobbly gook.

---

### Post by matt_symes on 2010-12-30
Hi

Try installing a new theme following the rest of the post. It may just be the theme you are using is corrupted.

Search on plymouth-theme in synaptic.

BTW: One of the themes did not work on my laptop.

Kind regards

---

### Post by steigerjb on 2010-12-30
> **matt_symes said:**
> Hi

Try installing a new theme following the rest of the post. It may just be the theme you are using is corrupted.

Search on plymouth-theme in synaptic.

BTW: One of the themes did not work on my laptop.

Kind regards

Didn't work.

The thing is, the manager errors when I try to launch it. My virtualbox ubuntu's plymouth manager works, it just looks really weird.

---

### Post by matt_symes on 2010-12-30
Hi

The thing is, i don't use Plymouth manager so i am not sure what is causing that problem.

Have you considered purging plymouth manager from your system?

Maybe, it's that which is causing the problem.

BTW: Did you get any error messages at any step when you installed new themes, selected a theme and ran the update command? Did each step complete successfully?

What was the output from sudo update-alternatives --config default.plymouth ? Did you see your newly installed theme?

Also, open a terminal and type

```
ls -l /etc/alternatives/default*
```

Post back results here

Kind regards

---

### Post by steigerjb on 2010-12-30
> **matt_symes said:**
> Hi

The thing is, i don't use Plymouth manager so i am not sure what is causing that problem.

Have you considered purging plymouth manager from your system?

Maybe, it's that which is causing the problem.

BTW: Did you get any error messages at any step when you installed new themes, selected a theme and ran the update command? Did each step complete successfully?

What was the output from sudo update-alternatives --config default.plymouth ? Did you see your newly installed theme?

Also, open a terminal and type

```
ls -l /etc/alternatives/default*
```

Post back results here

Kind regards

```
joe@joe-ubuntu:~$ sudo update-alternatives --config default.plymouth
[sudo] password for joe: 
There are 4 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                                             Priority   Status
------------------------------------------------------------
  0            /lib/plymouth/themes/space-sunrise/space-sunrise.plymouth                         200       auto mode
  1            /lib/plymouth/themes/INT2MIL-Ubuntu-10.10-Eng/INT2MIL-Ubuntu-10.10-Eng.plymouth   100       manual mode
  2            /lib/plymouth/themes/space-sunrise/space-sunrise.plymouth                         200       manual mode
  3            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth                             100       manual mode
* 4            /lib/plymouth/themes/ubuntu_plymouth_1010                                         100       manual mode

Press enter to keep the current choice[*], or type selection number: 


```

```
joe@joe-ubuntu:~$ ls -l /etc/alternatives/default*
lrwxrwxrwx 1 root root 41 2010-12-30 16:39 /etc/alternatives/default.plymouth -> /lib/plymouth/themes/ubuntu_plymouth_1010

```

---

### Post by steigerjb on 2010-12-30
how do i purge it?

---

### Post by matt_symes on 2010-12-30
Hi

Lets try setting to the default splash for plymouth, ubuntu-logo.plymouth

```
sudo update-alternatives --config default.plymouth
```

Type 3 and then press enter. Then type...

```
sudo update-initramfs -u
```

Your symbolic link is pointing to the theme ubuntu_plymouth_1010. This is not one i have seen. 

BTW: Is this on you VM or partition?

As for Plymouth manager did you install as a .deb file from here [https://launchpad.net/plymouth-manager/+download](https://launchpad.net/plymouth-manager/+download) ?

Kind regards

---

### Post by steigerjb on 2010-12-30
> **matt_symes said:**
> Hi

Lets try setting to the default splash for plymouth, ubuntu-logo.plymouth

```
sudo update-alternatives --config default.plymouth
```

Type 3 and then press enter. Then type...

```
sudo update-initramfs -u
```

Your symbolic link is pointing to the theme ubuntu_plymouth_1010. This is not one i have seen. 

BTW: Is this on you VM or partition?

As for Plymouth manager did you install as a .deb file from here [https://launchpad.net/plymouth-manager/+download](https://launchpad.net/plymouth-manager/+download) ?

Kind regards

Didnt work. Still no theme, just text gobbly gook. This is my partition. Plymouth in my VM looks weird. See attached pic

Yes, i got it from that link

---

### Post by 0N3 on 2010-12-30
What graphics card have you i had same problem theres a script fix for this

---

### Post by matt_symes on 2010-12-30
Hi

Alright. Lets try to purge plymouth manager. Maybe that's what is causing the problem.

The only issue is i am not sure of the name of the package so lets try to get lucky and hope it's called plymouth something.

Open a terminal and type

```
dpkg -l plymouth*
```

That is a small L in the switch. Post the results back here.

Kind regards

---

### Post by matt_symes on 2010-12-30
Hi

> What graphics card have you i had same problem theres a script fix for this

That may fix the resolution, but that does not explain the fact the plymouth theme cannot be changed. It's strange eh?

Kind regards

---

### Post by 0N3 on 2010-12-30
I couldnt change the theme either all i had was text if i changed the theme until this script

---

### Post by 0N3 on 2010-12-30
this will uninstall the script if it didnt work

---

### Post by matt_symes on 2010-12-30
Hi

It's certainly worth a try then. It uses the framebuffer doesn't it?

@OP. Fancy giving the script a try?

Kind regards

---

### Post by 0N3 on 2010-12-30
[http://zorin-os.webs.com/splashscreenmanager.htm](http://zorin-os.webs.com/splashscreenmanager.htm)

I found this also useful application and startup-manager i played with the resolution with startup-manager and bingo had it working perfectly any theme i install works perfect

---

### Post by steigerjb on 2010-12-30
> **matt_symes said:**
> Hi

Alright. Lets try to purge plymouth manager. Maybe that's what is causing the problem.

The only issue is i am not sure of the name of the package so lets try to get lucky and hope it's called plymouth something.

Open a terminal and type

```
dpkg -l plymouth*
```

That is a small L in the switch. Post the results back here.

Kind regards

```
joe@joe-ubuntu:~$ dpkg -l plymouth*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  plymouth       0.8.2-2ubuntu5 graphical boot animation and logger - main p
ii  plymouth-label 0.8.2-2ubuntu5 graphical boot animation and logger - label 
ii  plymouth-manag 0.9.2-1        Manage your Plymouth with ease!
un  plymouth-theme <none>         (no description available)
ii  plymouth-theme 0.8.2-2ubuntu5 graphical boot animation and logger - ubuntu
ii  plymouth-theme 0.8.2-2ubuntu5 graphical boot animation and logger - ubuntu
joe@joe-ubuntu:~$ 

```

---

### Post by steigerjb on 2010-12-30
> **0N3 said:**
> [http://zorin-os.webs.com/splashscreenmanager.htm](http://zorin-os.webs.com/splashscreenmanager.htm)

I found this also useful application and startup-manager i played with the resolution with startup-manager and bingo had it working perfectly any theme i install works perfect

I have to get my boot fixed before I can try something else.

---

### Post by 0N3 on 2010-12-30
steigerjb 

did you try the script?

---

### Post by steigerjb on 2010-12-30
> **0N3 said:**
> steigerjb 

did you try the script?

No, i haven't tried it yet. What is it supposed to do?

---

### Post by 0N3 on 2010-12-30
run the script and see i had same problems as you in  another post the thatscript worked for me i had 6 different themes installed none would work or changed i tried all of the above suggested to no effect have you a proprietary graphics aka Nvidia or ATI? If so its worth a try

---

### Post by 0N3 on 2010-12-31
Looked @ your youtube channel didnt realise you subscribed to my channel thought i recognised your name

---

### Post by matt_symes on 2010-12-31
Hi

> No, i haven't tried it yet. What is it supposed to do?

I am no expert on the script, but i believe it works for forcing Plymouth to draw the splash screen into a framebuffer at a defined resolution of 1280x1024.

I think it's worth a try.

Kind regards

---

### Post by 0N3 on 2010-12-31
the best resolution for me was 1024x768.

---

### Post by steigerjb on 2010-12-31
> **0N3 said:**
> What graphics card have you i had same problem theres a script fix for this

didnt fix it

---

### Post by matt_symes on 2010-12-31
Hi

```
ii  plymouth-manag 0.9.2-1        Manage your Plymouth with ease!
```

Alright. Lets try to remove the plymouth manager. Maybe this is what's causing the problem (but i would be surprised). It looks like it's installed as plymouth-manager.

From a terminal type

```
sudo dpkg --purge plymouth-manager
```

This will remove it completely.

Could you also post the output of

```
cat /etc/default/grub | grep -i cmdline
```

I have been looking through the output you have posted from various commands 

One of the entries is
 
joe@joe-ubuntu:~$ dpkg -l plymouth*
un  plymouth-theme <none>         (no description available)

This does not look right to me. Open a terminal and type

```
sudo dpkg --configure -a
```

Hopefully this will correct that problem.

I have to go now what with it being new years eve and all. However, tomorrow i will set up a VM and see if i can try and recreate this issue you are having with your themes and attempt to fix it, because i am not 100% sure what the problem is. This is, of course, if it has not been fixed by then.

Kind regards

---

### Post by steigerjb on 2010-12-31
> **matt_symes said:**
> Hi

```
ii  plymouth-manag 0.9.2-1        Manage your Plymouth with ease!
```

Alright. Lets try to remove the plymouth manager. Maybe this is what's causing the problem (but i would be surprised). It looks like it's installed as plymouth-manager.

From a terminal type

```
sudo dpkg --purge plymouth-manager
```

This will remove it completely.

Could you also post the output of

```
cat /etc/default/grub | grep -i cmdline
```

I have been looking through the output you have posted from various commands 

One of the entries is
 
joe@joe-ubuntu:~$ dpkg -l plymouth*
un  plymouth-theme <none>         (no description available)

This does not look right to me. Open a terminal and type

```
sudo dpkg --configure -a
```

Hopefully this will correct that problem.

I have to go now what with it being new years eve and all. However, tomorrow i will set up a VM and see if i can try and recreate this issue you are having with your themes and attempt to fix it, because i am not 100% sure what the problem is. This is, of course, if it has not been fixed by then.

Kind regards

```
joe@joe-ubuntu:~$ sudo dpkg --purge plymouth-manager
[sudo] password for joe: 
(Reading database ... 261460 files and directories currently installed.)
Removing plymouth-manager ...
Purging configuration files for plymouth-manager ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for menu ...
Processing triggers for python-support ...
joe@joe-ubuntu:~$ 

```

```
joe@joe-ubuntu:~$ cat /etc/default/grub | grep -i cmdline
joe@joe-ubuntu:~$ 

```

---

### Post by steigerjb on 2010-12-31
> **matt_symes said:**
> 

Hopefully this will correct that problem.

I have to go now what with it being new years eve and all. However, tomorrow i will set up a VM and see if i can try and recreate this issue you are having with your themes and attempt to fix it, because i am not 100% sure what the problem is. This is, of course, if it has not been fixed by then.

Kind regards

```
joe@joe-ubuntu:~$ su-to-root -X -c /usr/sbin/startupmanager
xrandr: Failed to get size of gamma for output defaultGenerating grub.cfg ...
ze of gamma for output defaultFound linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Grub2 detected
Usplash not detected
Splashy not detected
Traceback (most recent call last):
  File "/usr/sbin/startupmanager", line 54, in <module>
    main()
  File "/usr/sbin/startupmanager", line 51, in main
    SumGui()
  File "/usr/share/startupmanager/gtk_frontend.py", line 193, in __init__
    self.setup_widgets()
  File "/usr/share/startupmanager/gtk_frontend.py", line 202, in setup_widgets
    self.set_shared_grub_widgets()
  File "/usr/share/startupmanager/gtk_frontend.py", line 223, in set_shared_grub_widgets
    self.timeout_spinner.set_value(self.grub.get_timeout())
  File "/usr/lib/pymodules/python2.6/bootconfig/grub.py", line 91, in get_timeout
    timeout = utils.extract_number(line)
  File "/usr/lib/pymodules/python2.6/bootconfig/utils.py", line 64, in extract_number
    match = number_filter.search(line)
TypeError: expected string or buffer
joe@joe-ubuntu:~$ 

```

Could not having usplash be why I have no boot animation, just text gobbly gook? 

I went to install it from synaptic but it wants to remove A WHOLE BUNCH of stuff.

---

### Post by geekguy on 2010-12-31
I got a different shutdown image by installing the flares theme, but that didn't change my login screen like I wanted it to. You may have to tweak your plymouth dir or uninstall other themes to get it to work.
I don't think that your usplash/splashy problem is local to you, because I got to where you are right now and couldn't install them either. Hopefully the coming release will solve the problem.

---

### Post by steigerjb on 2010-12-31
> **geekguy said:**
> I got a different shutdown image by installing the flares theme, but that didn't change my login screen like I wanted it to. You may have to tweak your plymouth dir or uninstall other themes to get it to work.
I don't think that your usplash/splashy problem is local to you, because I got to where you are right now and couldn't install them either. Hopefully the coming release will solve the problem.

At this point, i don't care about installing a new boot theme. I just want to get the regular boot back.

---

### Post by matt_symes on 2011-01-01
Hi

> Could not having usplash be why I have no boot animation, just text gobbly gook? 

I went to install it from synaptic but it wants to remove A WHOLE BUNCH of stuff.

Pymouth replaced usplash (after xsplash) so this is not your problem if you are using 10.04 or 10.10. You are using 10.10 ?

Lets check the contents of your default grub file and make sure that is setup to display a splash. Post the output of...

```
cat /etc/defaults/grub
```

Also, in post 9 when we tried to change the splash to plymouth default did that actually update to use the new theme?

Post the output of...

```
update-alternatives --display default.plymouth
```

Kind regards

---

