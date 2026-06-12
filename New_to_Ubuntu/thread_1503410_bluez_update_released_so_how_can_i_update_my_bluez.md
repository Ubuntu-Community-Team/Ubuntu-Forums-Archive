---
title: "bluez update released so how can i update my bluez?"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by human75 on 2010-06-06
hi there.i am suffering with my bluetooth adapter(bultin toshiba satellite a210 laptop adapter) for ages.according to google a lot of people also suffering with bluetooth adapter problem.yesterday i lost my bluetooth adapter and now i can get it work again?questions are;
1-where is my bluetooth adapter gone?
2-how can i bring it back?
 i checked bluez homepage and i found update but tar.gz file so i do not know how can i update?also do you think it will help me to make it work my bluetooth adapter again?please guide me.what should i do?thanks for your help in advance..

---

### Post by human75 on 2010-06-07
no answer?no help?no one?

---

### Post by human75 on 2010-06-09
i think this forum gets dead:(can anybody recommend me another useful ubuntu forum which maybe i can find answer for my questions..thanks in advance

---

### Post by tom.swartz07 on 2010-06-09
I think it would help if we had more information..

what exactly do you mean that you lost your adapter? are you talking about your physical bluetooth dongle that plugs into your computer or are you talking about the menu applet on the panel?

Can you verify that it is still installed? Look in synaptic and verify.

Also, it is usually recommended that you use a repository to update an application, rather than installing source code from a downloaded .tar file.

---

### Post by human75 on 2010-06-10
> **tom.swartz07 said:**
> I think it would help if we had more information..

what exactly do you mean that you lost your adapter? are you talking about your physical bluetooth dongle that plugs into your computer or are you talking about the menu applet on the panel?

Can you verify that it is still installed? Look in synaptic and verify.

Also, it is usually recommended that you use a repository to update an application, rather than installing source code from a downloaded .tar file.
     thanks god! someone gave me response:)no i have no external bluetooth dongle.my satellite a210 has builtin bluetooth adapter.and it does not work anymore.when i start bluetooth manager it says "CONNECTION TO BLUEZ FAILED.Bluez deamon is not running, blueman-manager cannot continue."i uninstall bluez and reinstall but i did not help.actually it was working when i clean installed ubuntu 10.04.i search at google a lots of people having same problem but no working solution i found:(what can i do next?i do not want to re install my ubuntu.please help.thanks

---

### Post by nuke7 on 2010-06-10
> **human75 said:**
> thanks god! someone gave me response:)no i have no external bluetooth dongle.my satellite a210 has builtin bluetooth adapter.and it does not work anymore.when i start bluetooth manager it says "CONNECTION TO BLUEZ FAILED.Bluez deamon is not running, blueman-manager cannot continue."i uninstall bluez and reinstall but i did not help.actually it was working when i clean installed ubuntu 10.04.i search at google a lots of people having same problem but no working solution i found:(what can i do next?i do not want to re install my ubuntu.please help.thanks

I'm no guru, but did you try enabling the onboard bluetooth in bios before booting intu ubuntu? that way it sees your BT adapter and can manage it, otherwise it'll think that you don't have BT adapter plugged in. Tell me if it works... :)

---

### Post by human75 on 2010-06-10
> **nuke7 said:**
> I'm no guru, but did you try enabling the onboard bluetooth in bios before booting intu ubuntu? that way it sees your BT adapter and can manage it, otherwise it'll think that you don't have BT adapter plugged in. Tell me if it works... :)
it is already enabled.it works flawlessy with windows7 and it was working in ubuntu as well.3 nights ago i watched a movie i enabled my motorola bluetooth headphone.next day i try to connect again and bluetooth is dead:(i restarted my laptop nothing has came back.i uninstalled bluez and reinstall but no luck.there is something absolutely wrong with ubuntu maybe registry is corrupt ot settings i dont know.i am just beginner:)but i tried a lots of thing which i found on google nothing helped me:(i am getting really tired:(thx in advance for your help

---

### Post by nuke7 on 2010-06-10
what does the bluetooth says when you click on it in "preferences" ?

---

### Post by human75 on 2010-06-10
> **nuke7 said:**
> what does the bluetooth says when you click on it in "preferences" ?
applet does not appear on panel.at preferences when i click bluetooth manager it says "CONNECTION TO BLUEZ FAILED.Bluez deamon is not running, blueman-manager  cannot continue."this is the message i am getting.

---

### Post by nuke7 on 2010-06-11
"Bluez daemon is not running, blueman-manager cannot continue." - 
this is what i get if i don't start bluetooth 
before booting, in the bios.
in winxp (dual-boot) i have hotkeys to enable BT and wifi too.
They don't work under Ubuntu netbook. also, if you try to start the "standard", built-in BT manager it should say this:
(attached screenshot)
so i think your problem could be solved if you turn on BT in the 
BIOS before beginning the booting process. 
If you already tried that, I don't have any more suggestions :(

---

### Post by human75 on 2010-06-11
> **nuke7 said:**
> "Bluez daemon is not running, blueman-manager cannot continue." - 
this is what i get if i don't start bluetooth 
before booting, in the bios.
in winxp (dual-boot) i have hotkeys to enable BT and wifi too.
They don't work under Ubuntu netbook. also, if you try to start the "standard", built-in BT manager it should say this:
(attached screenshot)
so i think your problem could be solved if you turn on BT in the 
BIOS before beginning the booting process. 
If you already tried that, I don't have any more suggestions :(
yes same message i am also getting.how can i turn on BT in the BIOS?my toshiba does not have ant bluetooth settings at bios.my wireless and bluetooth use same key(front of my laptop) and it is aleady switch on.i dont know what should i do?

---

