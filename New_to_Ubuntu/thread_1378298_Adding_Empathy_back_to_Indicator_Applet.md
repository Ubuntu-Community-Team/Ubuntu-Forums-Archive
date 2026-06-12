---
title: "Adding Empathy back to Indicator Applet"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by littlewontons on 2010-01-11
Hi,

I am running Ubuntu 9.10 and I accidentally uninstalled empathy. I reinstalled it, but it doesn't go back into the indicator applet.

I have already added the line "/usr/share/applications/empathy.desktop" in the "/usr/share/indicators/messages/applications" directory in the file called empathy. 

When I turn on Empathy, the Empathy icon shows up in my panel, and not in the indicator applet. I couldn't find out what else I can do. Any suggestions?

---

### Post by Excedio on 2010-01-11
> **littlewontons said:**
> I have already added the line "/usr/share/applications/empathy.desktop" in the "/usr/share/indicators/messages/applications" directory in the file called empathy. 

 
It's odd that this did not work. I just tested it out myself with Thunderbird and it worked. Open a terminal and type in
```
empathy
```
See if that starts the program or if you get an error stating that this is the wrong command.

---

### Post by littlewontons on 2010-01-11
I typed in "empathy" and the shell gave me this:

```
(empathy:5306): GLib-WARNING **: g_set_prgname() called multiple times
```

empathy runs, but the Indicator Applet does not hide the Empathy logo and the mail icon does not flash when something in Empathy is happening. i.e When someone replies a message. Instead, the regular Emapthy logo flashes.

---

### Post by J V on 2010-01-11
tried reinstalling the indicator?

---

### Post by littlewontons on 2010-01-11
I have tried, I ended up doing a whole bunch of upgrades for a couple of lib*-dev libraries, and then the final one required me to uninstall "ubuntu-desktop". I'm not sure what other options I have out there. Do you think there is some way to configure Empathy or reset Indicator applet?

---

### Post by tom.swartz07 on 2010-01-11
> **littlewontons said:**
> I have tried, I ended up doing a whole bunch of upgrades for a couple of lib*-dev libraries, and then the final one required me to uninstall "ubuntu-desktop". I'm not sure what other options I have out there. Do you think there is some way to configure Empathy or reset Indicator applet?

You could try resetting your entire panel config file...
Usually I tell people to do that when they remove something that theyre not supposed to.

```
sudo rm -rf ~/.gconf/panel
```

This will remove any of the config files related to your panel, and when you log out and log back in, they will be rebuilt.

9 times out of 10 this fixes whatever people do to mess up their panel. Hopefully it'll fix yours!

---

### Post by J V on 2010-01-11
dont think so, I scoured gconf myself, coulden't find any settings on which apps the indicator looks for...

---

### Post by littlewontons on 2010-01-11
Removing "~/.gconf/panel" didn't work. My panel settings didn't reset. I forgot to check if there was a panel folder. I will look into how to reset the panel settings. Any other suggestions?

---

### Post by cyprys on 2010-05-07
Anyone solved this? There used to be "Use Message Indicators" in "Notifications" tab of Empathy preferences but I cannot find it any more. Anyone knows whether it has been moved or removed?

---

### Post by crjackson on 2010-05-07
What version of empathy are you using.  It's working fine for me as far as I can tell.

---

### Post by cyprys on 2010-05-07
Empathy 2.30.1

No... You don't get me. I do see all the notifications, that's not the case. The case is:

1. remove Empathy,
2. install it again,
3. there's no empathy in messages indicator applet

And when you open gedit, put in "/usr/share/applications/empathy.desktop" and save it in "/usr/share/indicators/messages/applications" there's a "Chat" entry in messages indicator applet, like it should be, but the Empathy itself uses separate icon in notification area.

"Use Message Indicators" used to disable this separate icon and make Empathy use messages indicator applet without placing any files anywhere manually.

---

### Post by crjackson on 2010-05-08
> **cyprys said:**
> Empathy 2.30.1

No... You don't get me. I do see all the notifications, that's not the case. The case is:

1. remove Empathy,
2. install it again,
3. there's no empathy in messages indicator applet

And when you open gedit, put in "/usr/share/applications/empathy.desktop" and save it in "/usr/share/indicators/messages/applications" there's a "Chat" entry in messages indicator applet, like it should be, but the Empathy itself uses separate icon in notification area.

"Use Message Indicators" used to disable this separate icon and make Empathy use messages indicator applet without placing any files anywhere manually.

Okay, I gotcha...  Mine has never been uninstalled and reinstalled, this is from a fresh install.  I have 12 machines running with a fresh install and ALL of them work without the "Use Message Indicators" option showing anywhere.  All I can think of is that it is a depreciated option.

I too get the second icon in the notification area when empathy is active.  I prefer it that way so It's not an issue here.

Sorry for misunderstanding your quandary.

---

### Post by cyprys on 2010-05-09
So, since this option is depreciated...  How to make reinstalled Emphaty use messages indicator instead of notification area?

Adding files to /usr/share/indicators/messages/applications creates only static entries in messages indicator, doesn't remove icons from notification area and doesn't capture the notifications itself.

---

### Post by Neovos on 2010-05-09
do you by any chance have the telepathy ppa added? Their version doesn't utilize the notifications. The upstream ppa version adds a patch that uses it. Check out this bug report: [https://bugs.launchpad.net/indicator-applet/+bug/470377](https://bugs.launchpad.net/indicator-applet/+bug/470377)

---

### Post by cyprys on 2010-05-15
**Neovos**, thank you! You're absolutely right.

For those with similar problem: testing new features of empathy is good but upstream version doesn't include patch to use "new messages" menu of the indicator applet.

To revert to the Ubuntu version of Empathy:
1. remove Empathy (don't purge so you wouldn't loose contacts history),
2. disable/remove the Telepathy PPA from sources,
3. **remove your apt cache** with *sudo apt-get clean*,
4. install Empathy again.

All your settings should prevail. Removing apt cache is important because if you don't and try to install Empathy again apt will install it from previously downloaded upstream package. I had some mano-a-mano time with that one.

Marking as solved. [color=green][edit: lol, forgot it's not my thread, sorry][/color]
Cheers!

---

### Post by kiddykoff on 2010-05-27
I had the same problem. just as an additional note, you will also have to remove empathy-common and nautilus-sendto-empathy. At least this was so in my case.

---

### Post by dre12b on 2010-08-08
Thanks to all for figuring this out - this was driving me crazy.  Anyway to continue using the upstream telepathy ppa AND use the message indicator?

---

### Post by koki on 2010-09-11
Just wanted to say that this did the trick for me. Thank you!

---

### Post by cyprys on 2010-09-11
> **kiddykoff said:**
> (...) you will also have to remove empathy-common and nautilus-sendto-empathy. At least this was so in my case.
That is correct - dependencies have to be removed.

---

### Post by cyprys on 2010-09-11
> **dre12b said:**
> (...) Anyway to continue using the upstream telepathy ppa AND use the message indicator?
I'm afraid the only way is to download the source code, apply the indicator patch and compile afterwards.

---

