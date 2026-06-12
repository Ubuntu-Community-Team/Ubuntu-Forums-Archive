---
title: "Changing icon for individual file."
date: 2011-05-24
forum: New to Ubuntu
---

### Post by Mccfuzz on 2011-05-24
As with Win2k  chose to use Thunderbird as my e-mail client.
However, I never liked the icon as it first glance it just doesn't say 'mail'!
In Windows I simply righted clicked on the Thunderbird icon and the resulting window can be found an option for changing the icon.  Simples.  I chose the envelope icon.
Is it possible to do the same with Ubuntu?

:confused:

---

### Post by kaldor on 2011-05-24
Desktop icon or the left launcher icon?

If it's a desktop icon, it's as easy as changing it like on Windows. On the new Unity UI, it's not as simple.

I think for Unity you'd need to modify the artwork yourself.

---

### Post by ngubk on 2011-05-24
What's the name of the icon package you use.
In my case, i use Farenza icon, so this is the process to change a certain Icon( it works in Unity Launcher for me too):

1/ open /usr/share/icon. find the icon package folder you're using.
2/ open the folder. in case of thunderbird it should be placed under the sub folder your_icon_package/app
3/change the thunderbird icon of every size ( 16, 32, scalable..) 
4/ logout -> the thunderbird icon should be change as you want

---

### Post by Anuovis on 2011-05-24
If you want to change a single shortcut, folder or file icon, that one is actually a button that lets you pick any picture. You can find this by right clicking on the object and going to *Properties*.

---

### Post by Mccfuzz on 2011-05-24
I'm a total novice with Ubuntu as I've only been using for a few days.
Consequently I don't understand some of the references you are alluding to such as 'unity' or 'Farenza Icon' etc.

I'll have to google the terms and enlighten myself.  Thanks for your replies.

---

### Post by ngubk on 2011-05-24
Then it can be a bit hard for you. I suggest you could change all of your icons. Here is a very beautiful icon package for you: open terminal , paste the following:
    1/sudo add-apt-repository ppa:tiheum/equinox
    2/sudo apt-get update && sudo apt-get install faenza-icon-theme

---

### Post by life in color on 2011-06-20
Hi, I installed faenza-darkest and I simply want to change all the folder icons from their beige color to like a bright green but I can't find the folder icon, I found about 4 home folder icons and one sharing folder icon but I couldn't find the regular folder icon. :( Any ideas?

---

