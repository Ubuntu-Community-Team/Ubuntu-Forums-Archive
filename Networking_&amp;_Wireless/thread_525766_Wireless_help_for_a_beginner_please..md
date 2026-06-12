---
title: "Wireless help for a beginner please."
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by wobwill on 2007-08-14
Hi All,

I am brand new to Ubuntu and could really use some help getting connected. Attached are copies of the readouts from the commands the files are named after. Any help or thoughts anyone has would be appreciated. Thank you in advance. The files are in .odf format but as this is the ubuntu site I thought it wouldn't be a problem. 

Will.

---

### Post by bmartin on 2007-08-14
See [this thread]("http://ubuntuforums.org/showthread.php?t=525833").

---

### Post by wobwill on 2007-08-15
Thank you for pointing me to that thread.

I installed wicd and then the other code but am completely unable to see wireless networks. 

Is there anything I can post that will give information to help people have a better idea of what's going on with my connection?

Will.

---

### Post by imdano on 2007-08-15
Were you able to see wireless networks before installing the new driver and wicd?

---

### Post by wobwill on 2007-08-15
Well,

Yesterday I spent several hours with a friend (ubuntu user) trying to get connected wirelessly. We were eventually able to connect for all of 2 minutes. At which point we restarted the computer and lost the connection. Since then I have been trying and failing repeatedly. The most I am able to see in Network Settings are 'connect to a hidden network' and 'create a wireless network'. 

Today I reinstalled Ubuntu (clean install). Having gone through the troubleshooting guide and getting lost at point three - iwconfig does not show a connection with the router, I was about to again follow the advice from bmartin. 

I currently have a wired connection and don't have any wireless options when I left click the icon in the top bar. When I open system/administration/network both a wired and wireless connection appear in connections and are ticked. In the wireless connection properties I have disabled roaming and have entered my wireless network settings. 

The command** lspci | grep Network** returns the following line.

**03:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)**

Is there anything else I should do before following the advice of bmartin

Will.

---

### Post by bmartin on 2007-08-15
You shouldn't be using the built-in wireless manager if you're using wicd.

If you installed wicd, you should be using wicd to manage your wireless settings. If you installed it from my page, you should be able to run it using the command **wicd** from a terminal. If you'd like an icon placed in your system tray, run **wicd-tray**.

---

### Post by wobwill on 2007-08-15
Hi bmartin

thanks for replying so quickly,

Since doing the reinstall I haven't followed any of your advice as yet. I was waiting for a reply. What i'll do now is go to your original thread and follow it through. Am I right in thinking that the installation process for wicd uninstalls network manager or do I need to do that as well? If so, how?

Will.

---

### Post by wobwill on 2007-08-15
Have gone to the wicd page and pasted the commands into a terminal. After the commands run I choose Y to continue and the process aborts. I have tried both upper and lower case and being a user and a super user. Any ideas?

Will

---

### Post by bmartin on 2007-08-15
You have to type the word **yes**. They do this as a security precaution.

Most repositories have a GPG key so that you can verify that the packages you get from a repository are authentic. Since that site doesn't have a GPG key (AFAIK), Ubuntu throws you a warning regarding the matter. I've contacted the development team regarding the manner.

network-manager should be automatically uninstalled. Let me know whether or not this is the case.

---

### Post by wobwill on 2007-08-15
Hi bmartin,

I don't know what I am doing wrong

Y, y, Yes, and yes all come back with a single line. Abort.

I have attached the terminal log, hoping that you can see something I can't. 

Will

---

### Post by bmartin on 2007-08-15
When it says
**Do you want to continue? [Y/n]**
Type Y or simply press enter.

It should prompt you to type **yes** after that.

---

### Post by wobwill on 2007-08-15
Hi,

I have no idea what has happened but my wireless card is flashing merrily away and I am connected. I am going to restart the computer and see if this lasts. 

Will.

---

### Post by wobwill on 2007-08-15
Hi,

I'm posting this via my wireless card after restarting my laptop. I have no idea what happened. I don't think I installed wicd, nor did I go on to use the fix. I have no idea what happened. I have been sitting here for the past couple of hours watching it and waiting for replies from the forum.  It has just started working!?! :confused:  I would be more than happy to post any terminal or other logs for people to review.

Thank you for replying to my posts and giving me the help you have. No doubt i'll be posting a lot more in the future! :lolflag:

Will

---

### Post by bmartin on 2007-08-15
That's how it always seems to go. Anyways, use what works for you. If you're curious about wicd or wifi-radar, check them out. They're simply other programs used to connect to wireless networks that many people consider to be superior to Gnome's built in software.

---

