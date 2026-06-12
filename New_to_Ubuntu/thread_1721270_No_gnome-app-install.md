---
title: "No gnome-app-install ?"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by BesouroLaranja on 2011-04-04
Good morning to all,

I've downloaded and installed ubuntustudio 10.04, but I can't seem to find the graphical aplication for installing programs. Can anyone help?


PS: Also I'm having trouble installing Nvidia 3d graphic acelerator drivers... Ubuntu says there is a hardware driver for it, but it's not capable of downloading it for me. Gives me the following: "Failed to fetch cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/pool/main/n/nvidia-settings/nvidia-settings_195.36.08-0ubuntu2_i386.deb File not found"

---

### Post by Jetro on 2011-04-04
I'm not sure this is what you mean, but you could try gdebi:

Type in a terminal:
```
sudo apt-get install gdebi
```

If it doesn't work, try right-clicking and go to "Open With" and see what the package opens with. Select GDebi Package Installer.

(I presume you're talking about .deb files here)

---

### Post by ~Plue on 2011-04-04
if you meant the package management utility, it'll be in menu > System > synaptic
(based from what i saw from screenshots, haven't experienced it personally)
if it isn't there, run* sudo apt-get install synaptic* and it should pop up in the above mentioned menu

for the nvidia issue, run *sudo apt-get update* from a terminal window (or reload from synaptic) and try again

---

### Post by BesouroLaranja on 2011-04-04
Thank you Jetro and thank you ~Plue, but it's not either gdebi or synaptic I'm looking for. It's some program installing facility that is usually under "Applications", much simpler to use than synaptic (wich is, I believe, a frontend to aptitude; I've already got both of them - synaptic and aptitude - but I don't know how to use them). Actually, I think what I'm looking for is called "Ubuntu Software Center". There's a screenshot of it here: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) and about every site I get on Google searches for "installing software ubuntu".

---

### Post by BesouroLaranja on 2011-04-04
Problem solved. It's called Ubuntu Software Center and I found it on Synaptic, with help provided here: [http://ubuntuforum-br.org/index.php/topic,81017.0.html](http://ubuntuforum-br.org/index.php/topic,81017.0.html) . Thank you everybody.

---

### Post by ~Plue on 2011-04-04
[s][QUOTE=BesouroLaranja][s]~Actually, I think what I'm looking for is called "Ubuntu Software Center"~ [/s][/QUOTE]
oh.. then do [I]sudo apt-get install software-center
[/I]if it doesn't show up in the main menu, add a new entry and use *software-center  *in the command field[/s]

///glad you got it solved

---

### Post by Jetro on 2011-04-04
> **BesouroLaranja said:**
> Problem solved. It's called Ubuntu Software Center and I found it on Synaptic, with help provided here: [http://ubuntuforum-br.org/index.php/topic,81017.0.html](http://ubuntuforum-br.org/index.php/topic,81017.0.html) . Thank you everybody.
Glad it worked out! ;)

Just so you know, Gdebi is a much lighter programme for installing .deb files you already have downloaded. But if you're happy, stick with it :)

---

