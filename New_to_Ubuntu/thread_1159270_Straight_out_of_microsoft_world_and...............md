---
title: "Straight out of microsoft world and.............."
date: 2009-05-14
forum: New to Ubuntu
---

### Post by idkwhat on 2009-05-14
I need help! I can not get myspace music players to work but youtube works fine! my dad has Ubuntu to and he can get the music players to work fine on Epiphany web browser but i cant! is there anything i need to download? i am an absolute noob so thanks for your patients!

---

### Post by HittingSmoke on 2009-05-14
> **idkwhat said:**
> I need help! I can not get myspace music players to work but youtube works fine! my dad has Ubuntu to and he can get the music players to work fine on Epiphany web browser but i cant! is there anything i need to download? i am an absolute noob so thanks for your patients!

I had problems with this on several of the myspace music player's first implementations but the current one they have up is working fine for me on the current versions of Firefox and Flash

---

### Post by idkwhat on 2009-05-14
> **HittingSmoke said:**
> I had problems with this on several of the myspace music player's first implementations but the current one they have up is working fine for me on the current versions of Firefox and Flash


what is the current versions you have? i believe i have the current stuff but the music players wont even show up let alone play for me

---

### Post by idkwhat on 2009-05-14
Can anyone tell me why myspace music players wont show up or play? i have been d/l audio filters and flash players all day and i cant figure this out!

---

### Post by Locutus_of_Borg on 2009-05-14
what is a "myspace music player"?

some kind of embedded device?

link me to one of them

---

### Post by HeirPixel on 2009-05-14
Have you tried opening a terminal a typing **sudo apt-get install flashplugin-nonfree** ?

---

### Post by Elfy on 2009-05-14
Threads merged. Please don't post the same question more than once.

---

### Post by HittingSmoke on 2009-05-14
> **idkwhat said:**
> what is the current versions you have? i believe i have the current stuff but the music players wont even show up let alone play for me

I'm using Firefox 3.0.10 (from the repos) and Flash 10. I don't use Epiphany so I can't speak for how well it does with Flash content

---

### Post by idkwhat on 2009-05-14
> **Locutus_of_Borg said:**
> what is a "myspace music player"?

some kind of embedded device?

link me to one of them

yeah its an embedded music player for adding songs on myspace

[http://www.myspace.com/victorsrumor](http://www.myspace.com/victorsrumor)

---

### Post by idkwhat on 2009-05-14
> **HittingSmoke said:**
> I'm using Firefox 3.0.10 (from the repos) and Flash 10. I don't use Epiphany so I can't speak for how well it does with Flash content


yeah imusing the same stuff...there must be a plug in im missing

---

### Post by idkwhat on 2009-05-14
> **HeirPixel said:**
> Have you tried opening a terminal a typing **sudo apt-get install flashplugin-nonfree** ?


i just tried it now im going to see if it worked lol thx

---

### Post by AndThenWhat on 2009-05-14
Press ALT+F2 and type "sudo apt-get install flashplugin-nonfree flashplugin-installer adobe-flashplugin" in the box and check the box that says "Run in a terminal". Then hit ENTER.

Next, put in your password in the window that pops up and after that command is finished running close Firefox and re-open it. Hopefully, you should be in business.

---

### Post by idkwhat on 2009-05-14
> **HeirPixel said:**
> Have you tried opening a terminal a typing **sudo apt-get install flashplugin-nonfree** ?


nope didnt work with firfox,epiphany, or seamonkey thx n e ways

---

### Post by idkwhat on 2009-05-14
> **AndThenWhat said:**
> Press ALT+F2 and type "sudo apt-get install flashplugin-nonfree flashplugin-installer adobe-flashplugin" in the box and check the box that says "Run in a terminal". Then hit ENTER.

Next, put in your password in the window that pops up and after that command is finished running close Firefox and re-open it. Hopefully, you should be in business.


didnt work and idk why nothing ops up after the command

---

### Post by AndThenWhat on 2009-05-14
Make sure you checked the box that says "run in terminal" and don't use quotes in the command above. If that doesn't work you might want to try uninstalling Firefox and re-installing it and then running the command above again.

---

### Post by idkwhat on 2009-05-14
> **AndThenWhat said:**
> Make sure you checked the box that says "run in terminal" and don't use quotes in the command above. If that doesn't work you might want to try uninstalling Firefox and re-installing it and then running the command above again.


yeah still nothin....is there anything on synaptic cause im used to using repositories

---

### Post by idkwhat on 2009-05-14
> **idkwhat said:**
> yeah still nothin....is there anything on synaptic cause im used to using repositories


yupp absolutely nothing works and im about to bang my head into a wall with frustration

---

### Post by mike555 on 2009-05-14
When you install flash, make sure Firefox is closed when you install it or it wont install in my experience , so if you go to;  [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)     .. download it and then close Firefox , then install ....

---

### Post by eilios on 2009-05-14
Have you tried "sudo apt-get install ubuntu-restricted-extras" ?

---

### Post by idkwhat on 2009-05-14
> **eilios said:**
> Have you tried "sudo apt-get install ubuntu-restricted-extras" ?

yes ive already done that...thx n e ways

---

### Post by albinootje on 2009-05-14
> **idkwhat said:**
> yupp absolutely nothing works

Which Ubuntu release is this ? I've read reports of users upgrading from Ubuntu 8.10 to 9.04 and needing to re-install flash because it 
stopped working.

Can you post the output of the following :
```

dpkg -l|grep -i flash
uname -a
lsb_release -r

```

And did you try it also in the Galeon browser ?

---

### Post by bacardiandwatermelon on 2009-05-15
I don't have install flashplugin-nonfree installed but it works fine. Try running sudo apt-get install adobe-flashplugin

---

### Post by james_mcl on 2009-07-11
I've just fixed a similar problem in Hardy (myspace music player didn't work in any browser, regardless of whether I used Gnash/Swfdec/Adobe, but Youtube was fine.)

If you go to your home folder, choose to view hidden files, and delete the .macromedia folder, then open your browser and head to Myspace, it may then work. I suspect that permissions for that folder or a subfolder have become corrupted - in my case, if a particular subfolder of that folder was set to read-only, Youtube worked fine but it Myspace Music Player was broken. If the folder isn't present, Flash will just generate a new, uncorrupted, one, though.

Incidentally, I recommend deleting that folder at the start of every session. It's only really used by the Flash plugin to store a sort of Flash version of a persistent tracking cookie that your browser can't delete, and a new one is created whenever you go to a page that uses Flash.

---

