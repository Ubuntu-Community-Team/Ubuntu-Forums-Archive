---
title: "wpasupplicant"
date: 2005-08-27
forum: Networking &amp; Wireless
---

### Post by Purgatory on 2005-08-27
Okay, so, I know I have to install it. And I know it's in the universe something or other. And I know you have to edit sources.list to enable the universe bit. But, being as how I'm really, really new to this all, I've a question on editing the file itself:

Even after chmod'ing the file to 777 (at least temporarily), when I try to save it after uncommenting the universe part (using gedit), I get an error about being unable to save the file. This has been a frustrating introduction for me, so pardon me if I missed threads concerning this during my albeit brief searches through the forums.

Thanks in advance.

---

### Post by sigma2805 on 2005-08-27
thats probably because you didn't try editing it as a temporary super user. 
create a backup first by typing sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup2
then try typing sudo gedit /etc/apt/sources.lst and enter your password. that should allow you to edit it and save it.

---

### Post by Purgatory on 2005-08-27
That did it. Awesome. Thanks a lot.

EDIT: While we're on the topic of wpasupplicant, I run the command the "How To" tells me to (sudo apt-get install wpasupplicant), but I get an error: Can't stat source package list.

---

### Post by sneax on 2005-08-27
go into synaptec and it will automaticaly refresh everything because you changed your sources.list

when it's done refreshing close synaptec and try the command again

there is a command for on the prompt too but i forgot it ... i think it's something like apt-get update but im not sure

---

### Post by Purgatory on 2005-08-27
[QUOTE=sneax]go into synaptec and it will automaticaly refresh everything because you changed your sources.list

when it's done refreshing close synaptec and try the command again

there is a command for on the prompt too but i forgot it ... i think it's something like apt-get update but im not sure[/QUOTE]
 When I open Synaptic I get the same error.

---

### Post by Purgatory on 2005-08-27
Sorry about the double-post, but I keep getting database errors when I try to edit my post. 

The exact error I get is:

> W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntudists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by sigma2805 on 2005-08-28
in the console type sudo apt-get update -that will update the packages database on your computer. Then open synaptic system->administration->synaptic package manager then search for wpa_supplicant and click on the check mark box and then choose mark for installation. Then push apply. that will download the application and install it.

---

### Post by Purgatory on 2005-08-28
[QUOTE=sigma2805]in the console type sudo apt-get update -that will update the packages database on your computer. Then open synaptic system->administration->synaptic package manager then search for wpa_supplicant and click on the check mark box and then choose mark for installation. Then push apply. that will download the application and install it.[/QUOTE]
 Oh, I see. You must be connectedin the Internet in the first place to install wpasupplicant? It's not a major problem, I just wasn't expecting that.

---

