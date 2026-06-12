---
title: "vmware local (turkish) characters doesn't work"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by redmorning on 2009-04-24
i searched vmware community forums and found a topic similar to mine but without a reponse.

i am running ubuntu 8.10 as host and two of my guest os are windows server 2003 and xp which works on vmware server 1.0.6 smoothly.At first i got a problem with up-down, ctrl, alt, shift, windows keys and fixed it but forgot how i did.I couldn't find any change in vmx file.

now i can't use my turkish characters on keyboard such as:
&#287; ü &#351; i ö ç

it is not a windows problem,i assure you,i am using vmware for a long time and all the selections are fine on windows os (language-keyboard)

can somebody help please,because that makes me slower.

---

### Post by redmorning on 2009-04-24
any idea?

---

### Post by MyR on 2009-04-24
I don't mean to be one of "those people" but I would recommend giving virtualbox a try if you can't get vmware working. [download here]("http://www.virtualbox.org/wiki/Linux_Downloads").

peace

---

### Post by redmorning on 2009-04-24
MyR,

thanks for your advice,i heard and read a lot about virtualbox but for now i want to think that as my last possibility,because i think i just need a couple of code to change/write to vmx file.

---

### Post by redmorning on 2009-04-25
problem solved,

i erased a line like "nokeymap" from /etc/vmware/config file that i added for the problem about  with up-down, ctrl, alt, shift, windows keys,instead of that i added those lines ([http://communities.vmware.com/thread/177321](http://communities.vmware.com/thread/177321)) :

#########################################

xkeymap.keycode.108 = 0x138 # Alt_R

xkeymap.keycode.106 = 0x135 # KP_Divide

xkeymap.keycode.104 = 0x11c # KP_Enter

xkeymap.keycode.111 = 0x148 # Up

xkeymap.keycode.116 = 0x150 # Down

xkeymap.keycode.113 = 0x14b # Left

xkeymap.keycode.114 = 0x14d # Right

xkeymap.keycode.105 = 0x11d # Control_R

xkeymap.keycode.118 = 0x152 # Insert

xkeymap.keycode.119 = 0x153 # Delete

xkeymap.keycode.110 = 0x147 # Home

xkeymap.keycode.115 = 0x14f # End

xkeymap.keycode.112 = 0x149 # Prior

xkeymap.keycode.117 = 0x151 # Next

xkeymap.keycode.78 = 0x46 # Scroll_Lock

xkeymap.keycode.127 = 0x100 # Pause

xkeymap.keycode.133 = 0x15b # Meta_L

xkeymap.keycode.134 = 0x15c # Meta_R

xkeymap.keycode.135 = 0x15d # Menu

##########################################

to /etc/vmware/config,save and quit;

everthing is fine now,maybe it helps somebody

---

