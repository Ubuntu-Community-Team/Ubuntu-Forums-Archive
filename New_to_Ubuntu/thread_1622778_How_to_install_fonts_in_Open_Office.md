---
title: "How to install fonts in Open Office"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by timbo59 on 2010-11-15
Hi there,
            Can anyone help me on a question of fonts? 

My wife, who's a professional writer and has worked with Word practically all of her working life, wants to keep working with it in Ubuntu, not least because all of the fonts she normally works with aren't available in Open Office.  I've tried installing Word on the computer via various instructions, but am absolutely clueless on what's being asked of me - I even had to look up what 'CD' meant in Ubuntu parlance! It didn't help - the instructions may as well have been in Greek. I've managed to transfer the appropriate files to the desk top, and that's where I ended.

Another tack was to try and find out why fonts such as Times Roman, Arial, Tacoma, etc, weren't on board Open office. Turns out that they were MS specific but are freely available to download. I found the following instructions but I still couldn't understand what it meant -*** You can install the MS core fonts by installing the [B]msttcorefonts** package. To do this, [enable the “Universe” component of the repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto"). This is done by default in Feisty.*[/B]

Where do I find this fonts package, how do I enable this Universe component - I could go on! I've been dealing with Windows for too long - that and/or I'm getting too old!

Thanks..........Tim

---

### Post by Verbeck on 2010-11-15
hi there

first, go to system>preferences>main menu and check the box next to 'software sources' if you are using maverick. if its lucid, skip to the next step
[IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=Software-Sources-hidden.png[/IMG]

then, go to system>administration>software sources and tick the check-box 'community maintained open-source software - universe'
[IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-UbuntuSoftware.png[/IMG]
then close the window and click reload when prompted

after that, open the software center or synaptic and search for [B]ttf-mscorefonts-installer



edit: [/B]to install fonts for the current user, create a new folder in your home directory called .fonts and copy all the font files there.
then, open a terminal (application>accesories>terminal) and run the command  [I]sudo fc-cache -f -v

[/I]more info : 
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by kaldor on 2010-11-15
Hey there,

I believe OpenOffice.org will use whichever fonts you have installed. To install the MS Fonts (system-wide), you do need to enable the Universe repository. The Universe repository is disabled by default because it is community maintained.

Enable it by doing this...

1) Click Applications on the top panel.
2) Click "Software Centre"
3) In Software Centre, click "Edit"
4) In the Edit menu, click "Software Sources".

You should have a window similar to the following:

[img]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-UbuntuSoftware.png[/img]

Enable the Universe repository by checking the box next to it.

To install the MS Fonts, open Terminal (Applications > Accessories > Terminal) and paste this command:

```
sudo apt-get install ttf-mscorefonts-installer
```

Enter your password to authenticate and it should then be installed.

Good luck to you and your wife :)

Edit: Beat me to it ;)

---

### Post by Old Marcus on 2010-11-16
Congrats to the both of you for bothering to give GUI instructions. It seems the community is becoming more user friendly. Woo! :D

---

### Post by timbo59 on 2010-11-16
Thanks to both for getting me there. It was a bit confusing, as the latest version of Ubuntu must be different to the one referenced above. When I went to System/Administrator there was no 'Software Sources' showing on the menu - maybe I just missed something. Anyway, through a combination of following both sets of instructions I finally found my way to where I needed to be, put in a search for **ttf-mscorefonts-installer **and it automatically installed once I clicked on it. Don't know why, but I didn't need that step suggested of opening up the terminal and inserting the recommended line of code. Whatever works, right?

Now all I have to do is wean my wife off Word and on to Open Office. 

As Old Marcus said, thanks for the GUI instructions. It made it so much easier for me to follow what was being stated. I think there's sometimes an assumption made that newbies like me understand basic elements to Ubuntu's inner workings that happily go sailing over my Windows-oriented head. First time I saw a reference to inserting code in the terminal, as an example, I thought 'what terminal'? Took me 10 minutes to figure it out. I'll get there eventually!

---

### Post by TNT1 on 2010-11-16
> **Old Marcus said:**
> Congrats to the both of you for bothering to give GUI instructions. It seems the community is becoming more user friendly. Woo! :D
+1
Well said.

---

### Post by kaldor on 2010-11-16
Not a problem :)

Edit: Oh, and for clarity:

> Anyway, through a combination of following both sets of instructions I finally found my way to where I needed to be, put in a search for ttf-mscorefonts-installer and it automatically installed once I clicked on it. Don't know why, but I didn't need that step suggested of opening up the terminal and inserting the recommended line of code. Whatever works, right?

Installing *ttf-mscorefonts-installer* via Software Centre is identical to using *sudo apt-get install ttf-mscorefonts-installer*. The command works like this:

"sudo" will grant you administration privelages

"apt-get" is the program that Ubuntu uses to install/remove/manage packages and software

"install" is the argument for *apt-get* that tells *apt-get* to install something

"ttf-mscorefonts-installer" is the package you wish to install.

So, if you wanted to **remove** the Fonts, you'd use *sudo apt-get remove ttf-mscorefonts-installer*.

The Software Centre is simply a GUI version of this. Maybe in time you'll end up naturally going to the Terminal to install or remove software. It happened to me :)

---

### Post by coffeecat on 2010-11-16
> **kaldor said:**
> To install the MS Fonts (system-wide), you do need to enable the Universe repository. The Universe repository is disabled by default because it is community maintained.

I've often seen this stated, but it's never been true for me, so I wonder if there is variation in a default install according to your geographical location. Agreed that in the live CD session the Universe and Multiverse repositories are not enabled, but in every permanent hard drive installation I've done for a long time, both the Universe and Multiverse repos have been enabled without me having to do anything. Back in Breezy days or thereabouts I think that was not the case, but more recently it has been here in the UK.

What happens in your part of the world?

---

### Post by VcDeveloper on 2010-11-24
Is the same procedure true for making **fonts** available for all applications?  I just received and **palaeo_hebrew.ttf** I want to insalll.  I already installed the **.he** font, but I want this **.ttf** also.

Do I just drop this file in /usr/share/fonts/truetype?

---

### Post by VcDeveloper on 2010-11-24
Cancel that! I found the answer on a google search here [**How to install TrueType fonts**]("http://www.arsgeek.com/2007/07/19/how-to-install-truetype-fonts-on-your-ubuntu-computer/").

---

