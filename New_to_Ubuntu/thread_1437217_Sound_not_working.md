---
title: "Sound not working"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by nnn= on 2010-03-23
Sound isn't working. My hardware should be fine. I need help getting it to work. If you need some information from me, instruct me how to find it.
[COLOR=Red]**Update**[/COLOR]: scroll down to post #8 or click here: [http://ubuntuforums.org/showpost.php?p=9021725&postcount=8](http://ubuntuforums.org/showpost.php?p=9021725&postcount=8)

---

### Post by n0dix on 2010-03-23
Did you check the sound is not muted?
Do in a console: alsamixer.

---

### Post by nnn= on 2010-03-23
I tried adjusting the settings in sound preferences, but to no avail. I have no sound at all. As far as I can see it's not muted. I also added my user to`group audio.

---

### Post by nnn= on 2010-03-23
I still need help.

---

### Post by lidex on 2010-03-23
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.
You can find a terminal in "Applications>Accessories>Terminal"

---

### Post by nnn= on 2010-03-23
I attached the file generated.

---

### Post by lidex on 2010-03-24
OK. Go to the alsa-upgrade-script link in my sig. Follow the instructions there to upgrade alsa to the latest version.

---

### Post by nnn= on 2010-03-24
Everything works now, except for meebo.com which is an online chatting app so I don't have use a separate app for messaging. There should be sound when somebody sends a message which is very important to me. I checked the sound troubleshooting page. There is sound in youtube videos for instance. If it's easier to use a separate client than to resolve this sound issue I could do that, but I'll need you to tell me what client that is. I'm anyway looking for a messenger that can play a sound file that I select instead of built-in ones.

---

### Post by nnn= on 2010-03-25
I still need help.

---

### Post by ThePinkWitch on 2010-03-25
> **lidex said:**
> OK. Go to the alsa-upgrade-script link in my sig. Follow the instructions there to upgrade alsa to the latest version.

Thanks Lidex..this totally fixed my sound issues :)

---

### Post by nnn= on 2010-03-25
I still need help.

---

### Post by lidex on 2010-03-25
I don't know...have you checked your meebo preference settings to make sure sound is enabled?

> IM Settings
To display your IM Settings:

   1. Click on preferences on your meebo page and choose IM Settings from the drop down menu
   2. Here you can set the following options by checking/un-checking the box to the left. Sound, IM History, Privacy and Emoticons

   1. Sound option for sending and receiving IM.
   2. IM History option to save or not save your chat log history.
   3. privacy option to receive messages from friends already on your buddy list.
   4. emoticons option to choose if you'd like to view as text or as emoticon.


Beyond that, you can try [empathy]("http://live.gnome.org/Empathy")
It's in the repos.

---

### Post by n0dix on 2010-03-25
or pidgin. In Linux you have other options.

---

### Post by nnn= on 2010-03-25
I added empathy, **checked settings** but it also has no sound. I tried opening the help for empathy but it takes forever to load.

---

### Post by lidex on 2010-03-25
Check this thread:
[http://ohioloco.ubuntuforums.org/showthread.php?p=7798156]("http://ohioloco.ubuntuforums.org/showthread.php?p=7798156")

---

### Post by nnn= on 2010-03-25
Can't find package sound-theme-freedesktop. There is ubuntu-sounds and ubuntustudio-sounds. It seems like there aren't any packages in ppa.launchpad.net/cheleb/ppa/ubuntu.
I checked pidgin and sound works, so I can use it.
I wonder why launchpad has lucid there and does not mention anything about it being a potential problem, especially since there is no such dir on the site.
Also why do I have to go advanced to edit effectively?

---

