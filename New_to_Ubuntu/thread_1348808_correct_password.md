---
title: "correct password?????"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Bellboy42 on 2009-12-07
Hello i have a Asus Eee Pc 701SD...linux.
 
When i try to enter the set up by pressing F2....I am getting the following message....
 
Enter CURRENT Password:
 
av entered password but nowt workin..after 3 tries it says ....
 
Password check failed
Press F1 to Resume..........
 
ANY HELP????.....Please.....

---

### Post by The_Pirate_King on 2009-12-07
First thing to do would be...check if caps lock is on. 

But let me get this straight... you're trying to enter your system BIOS to load the operating system?

---

### Post by Bellboy42 on 2009-12-07
> **The_Pirate_King said:**
> First thing to do would be...check if caps lock is on. 
 
But let me get this straight... you're trying to enter your system BIOS to load the operating system?
 
 
trying to enter it to alter bios to accept windows xp

---

### Post by adaucourt on 2009-12-07
> **Bellboy42 said:**
> Hello i have a Asus Eee Pc 701SD...linux.
 
When i try to enter the set up by pressing F2....I am getting the following message....
 
Enter CURRENT Password:
 
av entered password but nowt workin..after 3 tries it says ....
 
Password check failed
Press F1 to Resume..........
 
ANY HELP????.....Please.....

To reset password:

[LIST]
[*]Shutdown
[*]Power on and hit ESC at the grub prompt
[*]Finder your kernel and press 'e'
[*]Goto the line that starts with 'kernel' and press 'e'
[*]At the end add 'single' without the quotes
[*]Press Enter
[*]Press b to boot
[*]Once you see the menu choose "Drop to root shell"
[*]Change your password using "passwd newpassword"
[/LIST]

---

### Post by The_Pirate_King on 2009-12-07
Hmm... well, did anybody have the computer before you?  Because I believe you can set a separate password using the BIOS to secure your machine... 

I think you can reset the bios on most laptops by removing the battery and power cord and holding down the power button for about ten seconds.

---

### Post by Bellboy42 on 2009-12-07
> **adaucourt said:**
> To reset password:

[LIST]
[*]Shutdown
[*]Power on and hit ESC at the grub prompt
[*]Finder your kernel and press 'e'
[*]Goto the line that starts with 'kernel' and press 'e'
[*]At the end add 'single' without the quotes
[*]Press Enter
[*]Press b to boot
[*]Once you see the menu choose "Drop to root shell"
[*]Change your password using "passwd newpassword"
[/LIST]
Wat u mean by...at the GRUB PROMPT...wat is that?
and wats the KERNAL
 
Soz....can do a lot with pcs..but dont know these tech terms...just stuck on this machine... txs

---

### Post by Bellboy42 on 2009-12-07
> **The_Pirate_King said:**
> Hmm... well, did anybody have the computer before you? Because I believe you can set a separate password using the BIOS to secure your machine... 
 
I think you can reset the bios on most laptops by removing the battery and power cord and holding down the power button for about ten seconds.
 
just tried that...didnt work...txs anyway...

---

### Post by Bellboy42 on 2009-12-07
> **The_Pirate_King said:**
> First thing to do would be...check if caps lock is on. 
 
But let me get this straight... you're trying to enter your system BIOS to load the operating system?
 
 
caps are off

---

### Post by adaucourt on 2009-12-09
> **Bellboy42 said:**
> Wat u mean by...at the GRUB PROMPT...wat is that?
and wats the KERNAL
 
Soz....can do a lot with pcs..but dont know these tech terms...just stuck on this machine... txs

Sorry I misread, thought you were referring to lost GRUB password not BIOS.  Here is a link to open up your machine and unplug you CMOS battery.
[http://www.eeepcandme.com/how-to-open-your-eee-pc-case-eee-pc-mod-guide/](http://www.eeepcandme.com/how-to-open-your-eee-pc-case-eee-pc-mod-guide/)

---

