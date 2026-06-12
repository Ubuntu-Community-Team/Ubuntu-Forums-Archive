---
title: "big compiz problem"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by evets9 on 2011-08-30
im very new to ubuntu. i was advised to start using compiz, which i had a fiddle with. ive done something now i have no bar across the top, i have no icons down the left alt - f2 dosent work. Im talking to you now by using the 'download more backgrounds' feature through right hand clock on my desktop. that is all i can do.... please help     i think it sald something about tablet background before all the icons disapeared i cant remember.... please help...absolutley nothing works

---

### Post by sum1nil on 2011-08-30
From: [http://www.ubuntugeek.com/ubuntu-tip-how-to-reset-compiz-settings-to-default-system-settings-from-command-line.html](http://www.ubuntugeek.com/ubuntu-tip-how-to-reset-compiz-settings-to-default-system-settings-from-command-line.html)

[B]
Open the terminal and run the following command
    
gconftool-2 --recursive-unset /apps/compiz

Finally restart your system[/B]

I can't say I've had such a pervasive error before but maybe this will help.

---

### Post by evets9 on 2011-08-30
it says no such file...???  someone mention a kill gnome panel   what is that??

---

### Post by sum1nil on 2011-08-30
I got  "Command 'gconftool-2' from package 'gconf2' (main)"
so try: sudo apt-get install gconf2

this should install the program.

---

### Post by evets9 on 2011-08-30
i done what u said and nothing. i unistalled compiz and reinstalled it and done what u said and still nothing. its sooo frustrating. is there any way i can restore to a previous point or anything? or reinstall the whole of ubuntu again and i have no files saved on here so wont be no loss. or  anyother suggestions?

---

### Post by SNIFFER_dog on 2011-08-30
Hi evets9,

I think I did a similar thing to you, and I'm probably the same level of experience as you, but if you check my post it was solved by a helpful chap called [Krytarik]("http://ubuntuforums.org/member.php?u=1187548") from the Ubuntu Community.

Here is my post:

[http://ubuntuforums.org/showthread.php?t=1834691](http://ubuntuforums.org/showthread.php?t=1834691)

Check out this the two links that [Krytarik]("http://ubuntuforums.org/member.php?u=1187548") listed in his post and follow through them and that might help you out. There are some good tips to help along the way too.

Regards

SNIFFY

---

### Post by evets9 on 2011-08-31
thankyou ever so much, IT WORKED!!! i was pulling my hair out with anger last night, have had hardly any sleep and woke up to your solution. once again Thanks..!

---

### Post by SNIFFER_dog on 2011-08-31
No problem, glad I could help but the really thanks goes to  [Krytarik]("http://ubuntuforums.org/member.php?u=1187548")

SNIFFY

---

