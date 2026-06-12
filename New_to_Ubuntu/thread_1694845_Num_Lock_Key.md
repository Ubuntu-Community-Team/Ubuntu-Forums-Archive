---
title: "Num Lock Key"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by bug67 on 2011-02-24
Is it possible to have the Num Lock key enabled at boot?  I'd like it so that when I go to enter my password (which has some numbers that I use the numerical key pad for) I don't have to ensure it's active or not.  Not a *huge* deal just an extra step I'd rather eliminate.  TIA.

---

### Post by Kixtosh on 2011-02-24
It's a great question actually, and I have a very similar one, but I'll wait to see what responses you get before confusing the issue since I'm using a compact laptop where the keypad is integrated with other standard keys, whereas you are using a regular, full, keyboard, I presume.

---

### Post by bug67 on 2011-02-25
Shoulda done [this]("http://www.google.com/search?hl=en&biw=981&bih=632&&sa=X&ei=n-dnTaPlM4e6sAPEztWmBA&ved=0CBMQBSgA&q=enable+numlock+on+startup+linux&spell=1") in the first place. :D

Lots of good info. Imma try some of it when I get a chance. Will post the outcome here.
:popcorn:

---

### Post by bug67 on 2011-02-25
Found the answer right here on our own forums:

[http://newyork.ubuntuforums.org/showpost.php?p=8401687&postcount=11](http://newyork.ubuntuforums.org/showpost.php?p=8401687&postcount=11)

> **DarinB said:**
> Hey this worked it is fun when you get stuff to work.
Enabling NUM Lock at boot

The Default behaviour is for the NUM Lock key to be off at boot up, but if you wish to have it enabled for entering your login password, follow these instructions.

From Synaptic Package Manager, search for and install numlockx or, from the Terminal type or copy and paste:

```
sudo apt-get install numlockx
```

To get it working, you now have to edit the appropriate startup file. First, make sure you have a working backup of the file, in a Terminal type or copy and paste:

```
sudo cp /etc/gdm/Init/Default /etc/gdm/Init/Default.bak
```

Next, modify the gdm/Init file. In a Terminal type or copy and paste;

```
gksudo gedit /etc/gdm/Init/Default
```

Scroll down to the end of the file, and above the line that says “exit 0&#8243; add the following:

```
if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on
fi
```

Save the file then, next time you reboot, your NUM LOCK should default to “on".

Keeping Num Lock on afetr login:
Open [System], [Preferences], [Startup Applications], click on and type numlockx in the 1st box numlockx in the 2nd box and Keeps Num Lock on after login in the 3rd box, then click on [Add]. now restart your PC.

*copied from martin's ubuntu blog*

---

### Post by Kixtosh on 2011-06-22
It's been a while, but I just wanted to report back in case this could help anyone else. 

On a [COLOR=DarkRed]**Toshiba Portégé**[/COLOR] R200 series laptop (R205-S209), the keypad is integrated with other keys, and pressing the **Fn** key will give instant, "shift style operation" for typing numbers (similar to the way the Shift key instantly switches keys for typing capital letters). This is very convenient for random digits and zip codes, especially when using some foreign keyboard layouts (such as French for France) where **numbers on the top row** are NOT available without using the Shift key. The Caps Lock key only locks letter keys, NOT the top row. The problem is, for password logon, the Fn key defaults to the direction keys, not the keypad, so it's not nearly as convenient. Using the Caps Lock key, as explained, doesn't work. Using Shift for capitals means a clumsy two handed operation for any password with digits included. Using the keypad, without locking it, requires first pressing Fn and the keypad F12 combination, then letting go of F12, then pressing F12 again and letting go of both keys. This will finally activate normal keypad "shift type" behavior, and I hated it! Locking the keypad is only slightly more convenient, and only if all the numbers in your password are grouped together. You still have to unlock it to get back to typing normally. 

All of this fuss may seem like a small thing, but fast boot is one of the most immediately noticeable advantages of switching to Ubuntu from Windows, and this jumping over hurdles kind of defeats that impression.

The above procedure, explained by bug67, _cured everything in about two minutes_ flawlessly. The Fn now operates as a keypad shift key during logon, and the same behavior (already present by default), once the session has started has not been disrupted.

---

