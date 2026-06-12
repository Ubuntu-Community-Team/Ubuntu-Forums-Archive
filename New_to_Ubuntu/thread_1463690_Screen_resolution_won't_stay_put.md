---
title: "Screen resolution won't stay put"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by llmunro on 2010-04-27
Hello!

Every time I restart my computer, the screen resolution reverts back to some sort of setting that makes everything appear huge.  I can fix it by going to System>Preferences>monitor and manually changing it to 1024x768.  Is there a way to save the screen resolution I want so that when I log in, I don't have to readjust it every time?

Unrelated to this is another question about logging in after the computer has been idle.  Is there a way to turn off the option to have to log in every time the computer idles?  I realize this is for security, but I'm the only person who has access to my home computer and having to log in every time I'm away for five minutes is a bit of a drag.

Thank you!

Best,
Lisa

---

### Post by mikewhatever on 2010-04-27
> **llmunro said:**
> Hello!

Every time I restart my computer, the screen resolution reverts back to some sort of setting that makes everything appear huge.  I can fix it by going to System>Preferences>monitor and manually changing it to 1024x768.  Is there a way to save the screen resolution I want so that when I log in, I don't have to readjust it every time?

Can you tell us more about your system. What kind of graphics card is there. In case you aren't sure, run **lspci** in a terminal window and post the output

> Unrelated to this is another question about logging in after the computer has been idle.  Is there a way to turn off the option to have to log in every time the computer idles?  I realize this is for security, but I'm the only person who has access to my home computer and having to log in every time I'm away for five minutes is a bit of a drag.

Thank you!

Best,
Lisa

System->Preferences->Screen Saver. Uncheck the 'Lock the screen ...' box.

Regards, and welcome to the forum.

---

### Post by mbzn on 2010-04-27
As far as i know the auto log-off is enabled in the screensaver program... and can be changed there.

the resolution must be saved in /etc/xorg.conf for a perminent change

Hope this helps...

---

### Post by llmunro on 2010-04-27
Hello and thanks for the help!

Here's the terminal input about the graphics card:

lisa@lisa-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
lisa@lisa-desktop:~$ 


I'll try saving the current configuration as /etc/xorg.conf and restart to see if that works.

Thanks for all of the help!

Best,
Lisa

---

### Post by mbzn on 2010-04-27
Do you run Nvidia's driver (System>Admin>Hardware Drivers) or linux's?

For the Nvidia proprietary driver you could go to terminal and type

gksu /usr/bin/nvidia-settings

You should then be able to use the "Save to X Config file" button.

---

### Post by llmunro on 2010-04-27
Hi,

I tried saving the screen resolution that I wanted as /etc/xorg.conf and restarted my computer, but it reverted back to the wrong screen resolution.  (Perhaps I did it wrong?)

I looked at the drivers and have the NVIDIA accelerated graphics driver (current) [Recommended] selected.

Ran the gksu /usr/bin/nvidia-settings
and tried resaving the /etc/xorg.conf settings. 

Will try restarting again.

Thank you for the help!

Best,
Lisa

---

### Post by llmunro on 2010-04-27
No dice.  Screen reverts to the wrong settings on restart.

When I go to change the monitor resolution, I do get a message asking if I want to use my vendor's graphics card instead.  I click yes.  Does this have anything to do with it?

Thanks.
Best,
Lisa

---

### Post by Grenage on 2010-04-27
If in doubt, clear out your xorg and run the Nvidia tool again:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup
sudo touch /etc/X11/xorg.conf
gksu nvidia-settings
```

Ideally, you want to change the resolution settings using _only_ the nvidia-settings app.

I do have a [guide]("http://www.grenage.com/xorg.html") that covers manual xorg.conf configuration, but it shouldn't be at all necessary in your case.

---

### Post by llmunro on 2010-04-27
Thanks for the help!  I tried to run the code that you suggested, but found:

lisa@lisa-desktop:~$ mv /etc/X11/xorg.conf /etc/X11/xorg.backup
mv: cannot move `/etc/X11/xorg.conf' to `/etc/X11/xorg.backup': Permission denied


Am I doing this wrong?

Thank you!

Best,
Lisa

---

### Post by Grenage on 2010-04-27
I'm sorry, you'll need root access for that (oops).  I'll amend the code now.

---

### Post by mbzn on 2010-04-27
I can remember i,once after changing my screen i had to delete a file... i think it was called "monitors.xml". that did the trick back then. Somebody might be able to help with the correct name and location of the file.

---

### Post by mbzn on 2010-04-27
Here it is 
"Uncheck the "merge with existing file" when saving to xorg.conf
Also try deleting ~/.config/monitors.xml"

from this Thread [http://ubuntuforums.org/showthread.php?t=1313652&highlight=monitor+.xml](http://ubuntuforums.org/showthread.php?t=1313652&highlight=monitor+.xml) post #5

---

### Post by llmunro on 2010-04-27
Thanks to all!

I've unchecked the "merge with existing file option", but I'm not clear where I find the ~/.config/monitors.xml file in order to delete it.

Thanks again for all of your suggestions!

Best,
Lisa

---

### Post by Easy Limits on 2010-04-27
> **llmunro said:**
> When I go to change the monitor resolution, I do get a message asking if I want to use my vendor's graphics card instead.  I click yes.  Does this have anything to do with it?

Try clicking NO.

---

### Post by Grenage on 2010-04-28
So by clearing out the old xorg.conf, running the nvidia-settings tool (as root) and saving the new configuration ('Save to X configuration')...

..does your resolution still not persist through reboots?

---

### Post by sadaruwan12 on 2010-04-28
I also had the same problem with my nVidia VGA drivers. To over come that what I did was ran the vendors configuration utility and didn't save the xorg.conf from that utility 'cos it doesn't run with the root privileges.

So what to you do is set your desired resolution and the refresh rate for your monitor and clcik apply to get it applied after that there's option to (or a button) save the new configurations to a new xorg.conf file.

Before saving the tool provides function to get a preview of the new xorg.conf file which has been created from the nVidia tool.

Click that select all of the content and copy it on to a text file and save it as newxorg.conf on your desktop. After copying close the nVidia tool and run the below commands in your terminal.

This will backup your old xorg.conf file just in case:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup
```

Now you have a backup of your original xorg.conf. Now run this to open up the xorg.conf file in a text editor where you can see the configuration in plain text.

code:
```
sudo gedit /etc/X11/xorg.conf
```

You'll see a text file open up with multiple lines.

Select everything and delete it. Now open the newxorg.conf which we saved earlier on to the desktop and select the full content and pat it on to the xorg.conf file now now save that file close the programs reboot your system.

Thats it your system want change the resolution again if this doesn't work please let me know.

This might help you if your usig the new Ubuntu 9.10 version [Click Me]("http://sathyasays.com/2008/10/26/how-to-tackle-screen-resolution-problems-in-linux/")

Also when you're requesting help in future please mention the Ubuntu distribution version you're using, so we can be more help.

---

### Post by Grenage on 2010-04-28
> **sadaruwan12 said:**
> code:
```
sudo gedit /etc/X11/xorg.conf
```

Generally, people should use *gksu* rather than sudo when running a GUI app with root privileges.

---

### Post by sadaruwan12 on 2010-04-28
> **Grenage said:**
> Generally, people should use *gksu* rather than sudo when running a GUI app with root privileges.

Well bro you're right but this worked for me for ages thats why I posted it like that.

---

### Post by Immolatus on 2010-04-28
you need to add the resolution you want to the default list in Xorg.conf. Just make sure your monitor supports it. You can even go so far as to delete the other defaults to give it only one choice to force it, although this is generally not recommended.
Don't forget to save changes.:guitar:

---

### Post by llmunro on 2010-04-29
Wow! This thread has been growing in my absence!

I am pleased to report that the problem appears to be solved.  As Easy Limits suggested, I clicked "no" on the thing about the vendor's graphics card, got a box asking about monitor resolution, set my preferences, clicked apply y voila!  I've tested this through restarting and it seems to work!

Thanks to all for your suggestions, help, and time!  I'm always super impressed by how helpful people are here and I learn at least eight new things about Linux every day.

Happy Thursday!

Best,
Lisa

---

### Post by selfcommander on 2012-04-25
> **llmunro said:**
> Wow! This thread has been growing in my absence!

I am pleased to report that the problem appears to be solved.  As Easy Limits suggested, I clicked "no" on the thing about the vendor's graphics card, got a box asking about monitor resolution, set my preferences, clicked apply y voila!  I've tested this through restarting and it seems to work!

Thanks to all for your suggestions, help, and time!  I'm always super impressed by how helpful people are here and I learn at least eight new things about Linux every day.

Happy Thursday!

Best,
Lisa

yes basically the same thing this guy said  [http://ubuntuforums.org/showpost.php?p=7490352&postcount=2](http://ubuntuforums.org/showpost.php?p=7490352&postcount=2) 
worked for me too

---

