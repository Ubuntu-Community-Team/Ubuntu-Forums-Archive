---
title: "Mapping Superkey(windowskey) to numpad Enter"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by madsjuul on 2011-07-14
Hi
I just moved from Windows to Ubuntu(and is loving it)
On Windows I used to have the Windows key mapped to my Numpad Enter key
and used "sharpkeys" by raandy ranrz to do it. 
 Can you help me  to do the same on Ubuntu?

- Mads Juul

---

### Post by idoitprone on 2011-07-14
this is something i wrote on the spot, if it does not work change KP_Enter with return.

If that also does not work reboot then post output of

```
xmodmap -pke | grep -i "super"

``````
xmodmap
```save this code blow to a file
```
! change the left super key with kp_enter
clear mod4
keycode 133 = KP_Enter
```then

type 
```
xmodmap filenameorwhateveryoucalledit
```To make it start on boot. I am too lazy to type the answer rite now

---

### Post by Peter09 on 2011-07-14
Install compiz-config-settings-manager (ccsm). When you run it go to the desktop section and from there to Unity, there are key-mapping options in there.

---

### Post by madsjuul on 2011-07-14
Thank you idiotprone
I type this code in terminal 

xmodmap -e 'keycode 104=Super_L'

And it does what I want. To make it do it at startup I thought about putting it at a shell script i have running at startup to configure my Wacom board

-Mads

---

### Post by idoitprone on 2011-07-14
you might want to add

xmodmap -e "add mod4 = Super_L"

since the super key is a modfier key 

i was reading your thread absolutely wrong lol

---

