---
title: "Uninstalling all programs at once?"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by 2eki on 2011-08-19
Is it possible to uninstall all programs in ubuntu with a single click? (or terminal line?)

---

### Post by mr_luksom on 2011-08-19
What do you mean 'all programs'?

Formatting your hard drive is one way of 'uninstalling all programs'.

---

### Post by westie457 on 2011-08-19
> **2eki said:**
> Is it possible to uninstall all programs in ubuntu with a single click? (or terminal line?)

Hello. Welcome to the Forums.

The question is a bit vague.

Do you mean just the programs installed? Or do you mean everything installed including the kernels?

---

### Post by grahammechanical on 2011-08-19
They say a little knowledge is a dangerous thing. Here is a little knowledge for you.

Open Synaptic Package Manager. Scroll through the list of packages. Installed packages have a green box to the left of the line. If you want to remove or uninstall that package, click on the line and select Mark for Complete Removal.

Work your way down the list marking for removal those packages you wish to remove. When you are ready, click Apply and away they go.

It is not exactly removal with a single click but it is removal all at once. I am not sure that you can do this with the Ubuntu Software Centre.

Also remember, actions such as installing and uninstalling, however it is done, will require a password that gives the user these privileges. Is this what you are worried about? Someone messing with your system without your approval?

Regards.

---

### Post by corncob on 2011-08-19
> **grahammechanical said:**
> They say a little knowledge is a dangerous thing. Here is a little knowledge for you.

Open Synaptic Package Manager. Scroll through the list of packages. Installed packages have a green box to the left of the line. If you want to remove or uninstall that package, click on the line and select Mark for Complete Removal.

Work your way down the list marking for removal those packages you wish to remove. When you are ready, click Apply and away they go.

It is not exactly removal with a single click but it is removal all at once. I am not sure that you can do this with the Ubuntu Software Centre.

Also remember, actions such as installing and uninstalling, however it is done, will require a password that gives the user these privileges. Is this what you are worried about? Someone messing with your system without your approval?

Regards.

My Synaptic lists 30,699 packages -- that will keep you busy for a while lol.  You might take a look at System > Administration > Computer Janitor and see if that's what you want.  I don't know if it comes with 11.04 though, if that's what you're using.

---

### Post by donkyhotay on 2011-08-19
As mentioned previously your question is a little vague. Package managers don't make a distinction between libraries and programs. Although it's an obvious difference to us as users there is no real difference to the computer. Also many programs (not just libraries) on the system are ones people would consider to be part of the normal operation of the computer. A good example would be X. It's what handles your GUI and without it gnome or KDE won't work right meaning you're down to the CLI (command line interface). Technically I think you could (try) to uninstall the linux kernel but of course without a kernel you're computer won't boot. If there is a program on you're computer you don't like then just remove it from the software center but (as mentioned previously) the only way to remove "all programs" would be to essentially reformat.

---

### Post by 2eki on 2011-08-20
Sorry about the vague question. I want to remove all the extra software that comes with a new install of ubuntu, with a single click. I guess I can use Ubuntu Tweak, that is pretty helpful. 

Thanks for the advice! Also if anyone is interested in helping me further I have a question regarding compiling a linux kernel on lubuntu - [http://ubuntuforums.org/showthread.php?p=11169435#post11169435](http://ubuntuforums.org/showthread.php?p=11169435#post11169435)

---

### Post by corncob on 2011-08-20
I think I see what you mean -- there are a lot of apps in the Applications menu that you never use.  If that bothered me I would remove them one by one in the Software Center as I got to them.  Fortunately there is no one-click method -- you want to be selective here or your computer won't run.

---

### Post by SoFl W on 2011-08-20
Isn't there a very minimal ubuntu distro?  I forget the name.

---

### Post by Basher101 on 2011-08-20
Instead of scrolling through your whole packages, use the search function of Synaptic. On the left click on "installed" and then in the upper right is a search bar. Type the name of your programs you want to uninstall there and only those packages will be shown. thats the fastes way to get rid of those preinstalled programs

---

### Post by corncob on 2011-08-20
> **SoFl W said:**
> Isn't there a very minimal ubuntu distro?  I forget the name.

Are you thinking of Ubuntu Light?
[http://lifehacker.com/5535583/first-look-at-ubuntu-light-and-unity-the-super-fast-mac+like-netbook-os](http://lifehacker.com/5535583/first-look-at-ubuntu-light-and-unity-the-super-fast-mac+like-netbook-os)
It appears that that's only available to OEMs as a secondary operating system to get you connected fast but doesn't have much for features.
Similar might be Lubuntu (Light UBUNTU???) but the OP is aware of that already.

---

### Post by Basher101 on 2011-08-20
The "L" in (L)Ubuntu comes from the Desktop Environment it uses. It uses LXDE, thats where the "L" comes from..just like (X)Ubuntu (XFCE) and (K)Ubuntu (KDE)

---

### Post by Frogs Hair on 2011-08-20
You could consider the minimal installation also .[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by corncob on 2011-08-22
> **Frogs Hair said:**
> You could consider the minimal installation also .[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Here's a related thread:
[http://ubuntuforums.org/showthread.php?t=1830639](http://ubuntuforums.org/showthread.php?t=1830639)

---

### Post by Ozitraveller on 2011-08-22
HowTo Achieve "Ubuntu-Desktop-Minimal"
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by 2eki on 2011-08-28
Those two threads pretty much answered my questions thanks!

---

