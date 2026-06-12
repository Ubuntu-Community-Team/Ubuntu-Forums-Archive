---
title: "Where are my Programs?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Jerriy on 2009-01-20
I downloaded audio player programmes and I wanted to configure default applications as to what Firefox should do with the various media types.

The problem is that the newly installed player programmes (mplayer & vlc-player among others) don't show up in Firefox (the prefrences' default-application-chooser area).

So I select the "use other" option which openes the file manager (default "home")........... then what? What should happen next? 

I therefore also have two other questions regarding Ubuntu installation method in general:

- Where is the Ubuntu's equivalent of Program file if there is one - i.e. the default file of the installed programs (as I have never selected the destinations  myself, synaptic seems to do the selecting)? 
- What are Ubuntu's excutables ("exe" equivalent)?

Thanks in advance

---

### Post by hyper_ch on 2009-01-20
very likely they are in /usr/bin... mplayer should be /usr/bin/mplayer ... vlc is is a bit different...

You have them listed in your menu, right? Edit the menu and then you see the path.$

Normally you don't even need to specify the fullpath, you could just enter "mplayer".

And ubuntu doesn't depend on such stupid things like a file extension to define whether a file can be executed or not. Instead it uses file modes for that. You have to make a file executable by assigning it the proper permissions.

---

### Post by Jerriy on 2009-01-20
Thanks for the reply

Yes the programs are listed in the menu (in "applications") but that is a comand prompt (for example VLC's is "vlc %f" - but firefox's "use other" option insists for me to go to a particular folder. What should I do?

---

### Post by hyper_ch on 2009-01-20
then the command is just "vlc"

---

### Post by ugm6hr on 2009-01-20
> **hyper_ch said:**
> then the command is just "vlc"

You can just type it like that.

If you insist on finding it, it will be in:
/bin or or /sbin or /usr/bin or /usr/sbin

As mentioned, most are in /usr/bin

---

