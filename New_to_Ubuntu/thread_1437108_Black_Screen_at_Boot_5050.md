---
title: "Black Screen at Boot 50/50"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-03-23
When I boot my laptop, whether a cold boot or a warm boot, 50% of the time it hangs at a black screen. I've tried pressing alt+f2, but this doesn't work. The only key combination that seems to work is ctrl+alt+delete, and when I press these keys, it shows the bios almost instantly without shutting down properly. This must be terrible for my laptop.

I looked into reconfiguring xorg, but on 9.10 everything is automatic now. Plus, I don't know if that'd work. Just to be thorough, I have an Dell Inspiron 1525 and an Intel card.

---

### Post by EnigmaticCoder on 2010-03-23
bump

---

### Post by tommynz1975 on 2010-03-23
I am wondering if this is a dell issue as have had this happen lots my self
with grub. not grub 2. editing menu.lst..   maybe some one can give the grub 2 equvilant and instructions..

Below when he speaks of [SIZE=4]kopt=root=[/SIZE][SIZE=4]UUID=4efbf7b3-[/SIZE][SIZE=4]1188-4769-[/SIZE][SIZE=4]8e69-e9e131ac19[/SIZE][SIZE=4]36 ro reboot=b
the uuid is that users hard-drive yours will be a different set of letters/numbers
[/SIZE]
I found 


I have now found that  reboot=b has worked for many.

and should give this a try. As this bug was from 2007, I wonder does grub-2 fix ths at all?

cheers

Tom
 	Quote:
 	 	 		 			 				[Mark Favas]("https://launchpad.net/%7Emark-favas")             wrote             on 2007-09-08:                                                             [ #13]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131292/comments/13") I can make it reboot successfully by adding "reboot=b" to the grub kernel line in menu.lst:
 kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4efbf7b3-1188-4769-8e69-e9e131ac1936 ro quiet splash reboot=b

			 		 	 	 
 	Quote:
 	 	 		 			 				[Krzysztof Foltman]("https://launchpad.net/%7Ekfoltman")             wrote             on 2007-09-10:                                                             [ #15]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131292/comments/15")                                                        [SIZE=4]Yes, reboot=b helps. Thanks.[/SIZE]
 [SIZE=4]BTW: doing it the way that Mark Favas pointed out is not the optimal solution - because it doesn't survive running the update-grub script.[/SIZE]
 [SIZE=4]I've found that the more bulletproof way would be to add it in the commented out (!) kopt line, and run update-grub. Like this:[/SIZE]
 [SIZE=4]# kopt=root=[/SIZE][SIZE=4]UUID=4efbf7b3-[/SIZE][SIZE=4]1188-4769-[/SIZE][SIZE=4]8e69-e9e131ac19[/SIZE][SIZE=4]36 ro reboot=b[/SIZE]
 [SIZE=4]Yes, it's a commented out line and in spite of that, it seems to be used by update-grub for generating the proper entries. Luckily it's all well documented in the "stock" menu.lst.[/SIZE] 			 		 	 	 
source
[https://bugs.launchpad.net/ubuntu/+s...22/+bug/131292]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131292")

---

### Post by EnigmaticCoder on 2010-03-26
This is still an issue for me. I'm not sure I understand your instructions. Can you be more specific?

EDIT: There is no menu.lst in Grub 2

---

### Post by EnigmaticCoder on 2010-03-27
One last bump. Let's hope this is at least fixed in the next version of Ubuntu.

---

