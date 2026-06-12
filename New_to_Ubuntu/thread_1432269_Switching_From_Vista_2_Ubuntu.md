---
title: "Switching From Vista 2 Ubuntu"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by amnite on 2010-03-17
I am a Vista user and have been looking at Ubuntu th past couple months. I have it installed within Vista ATM. There are a few things/questions I have to hopefully bring the aspects of Vista I do like to Ubuntu and hopefully ween myself off of Vista completely. Im not sure of my exact version of Ubuntu but I downloaded it about a year ago...
1. Trash Bin/Computer location - Im trying to make a link to the trash bin and computer on my desktop. I know how to make a link but dont know of the program whereabouts.
2. Aero Glass - I also enjoy the visual appeal of Vistas "Glass Effect". Can I edit transparency through appearance, or do i have to find the files, etc where that sort of thing is kept and tweak it? If the last anyone know where i should start looking?
3. Windows SideBar - I loved the sidebar and its widgets. Is there any sort of thing available on Ubuntu?

I'll keep looking deeper for answers but if you know please reply. Thx

---

### Post by leandromartinez98 on 2010-03-17
Concerning the sidebar, I think you can try the gdesklets package. 

The transparency I think can be tuned if you use Compiz and install
the compiz settings manager, there are a lot of options there. But I'm
not sure.

---

### Post by Calash on 2010-03-17
For the trash try the following


Open a terminal

Type gconf-editor
Double Click on "Apps" to expand
Scroll down and click on "nautilus" to expand
Click on "Desktop" to get the options on the right.

Click the checkbox for "trash_icon_visible" and it will show up.


You can also turn on Network Places and My Computer (Using the windows terms for clarity)

---

### Post by dragonboss on 2010-03-17
1. Computer can be dragged onto the desktop from the places menu and for the trash ubuntu tweak can put it on the desktop for you
2. Install emerald theme manager
3. Screenlets or gDesklets

---

### Post by amnite on 2010-03-17
I downloaded installed compiz but cannot locate it in the menu. It said something about being for kde... could that have something to do with it.
 gdesklets is what i am looking for. any idea on where to look for more gadgets or a guide on how to build them?
gconf-editor worked great, can i also use it to prevent whats in my cd tray from showing up on my desktop

one extra question i remember while trying this stuff... i downloaded codecs for mp3 and mpg for my player and it still isnt working?

---

### Post by Tahakki on 2010-03-17
You want the program compizconfig-settings-manager, I think.

---

### Post by howefield on 2010-03-17
> **amnite said:**
> I downloaded installed compiz but cannot locate it in the menu. It said something about being for kde... could that have something to do with it.

You want the compizconfig-settings-manager package. Which you'll find in the System > Preferences menu once you have installed it.

There is also simple-ccsm which has fewer settings to control/tweak.

---

### Post by amnite on 2010-03-17
ok got compiz to work and gonna go mess with it.... thx alot peepz

---

### Post by Tahakki on 2010-03-17
Haha, no problem. As for 'glass', the next-next version of Ubuntu (after Lucid, which comes out in april) will have transparency built-in.

---

### Post by leandromartinez98 on 2010-03-17
> **amnite said:**
> 
one extra question i remember while trying this stuff... i downloaded codecs for mp3 and mpg for my player and it still isnt working?

Install the ubuntu-restricted-extras package, it should provide most of the plugins you may want.

---

