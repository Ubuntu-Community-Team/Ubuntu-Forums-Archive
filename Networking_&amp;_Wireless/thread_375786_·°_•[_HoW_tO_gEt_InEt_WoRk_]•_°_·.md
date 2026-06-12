---
title: "·° •[ HoW tO gEt InEt WoRk? ]• ° ·"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by cannabis on 2007-03-04
[FONT="Comic Sans MS"][COLOR="Blue"][SIZE="2"]Hello people!
I asked yet about my problem .. but there was no repleis at all. I need to configure cable connection that uses username and password. 
**So problem:**
 I have installed Ubuntu 5.10 and then Xubuntu 6.10 and its about 6 days Im sitting without Inet. :( XUbuntu cant detect [[COLOR="Red"]my NetworkCard[/COLOR]]("http://www.alliedtelesyn.com/products/detail.aspx?pid=238&lid=71"). Here is my 
```
lspci
``` 
[http://img215.imageshack.us/img215/4761/dsc043586rg5.jpg](http://img215.imageshack.us/img215/4761/dsc043586rg5.jpg)

```
sudo ifconfig -a
```
[http://www.imagehosting.com/out.php/i295331_DSC04371.GIF](http://www.imagehosting.com/out.php/i295331_DSC04371.GIF)


Please, I really need get it to work.

Thank You!

P.S. Here is some manual about how to install driver via Linux but there is no my version of card ... 

[ [IMG]http://www.imagehosting.com/out.php/t295415_Image3.gif[/IMG]](http://www.imagehosting.com/out.php/i295415_Image3.gif) 

[/SIZE]
[/COLOR][/FONT]

---

### Post by koenn on 2007-03-04
According to this list ( [http://www.faqs.org/docs/ethernet/Ethernet-HOWTO-4.html](http://www.faqs.org/docs/ethernet/Ethernet-HOWTO-4.html) ) your NIC uses a driver named rtl8139

I think you can load it by adding it to /etc/modules. I'm not sure, but I think you just add the driver name to the file.
If that doesn't work, try adding this instead:
```
alias eth0 rtl8139
```

Reboot and run ifconfig again.

---

### Post by finferflu on 2007-03-04
If you post questions using that type of characters it's more than obvious that people will not even read your post. You need to be as precise as possible writing the title of your posts, and avoid any useless, distracting character... That's my suggestion...

---

### Post by cannabis on 2007-03-04
> **finferflu said:**
> If you post questions using that type of characters it's more than obvious that people will not even read your post. You need to be as precise as possible writing the title of your posts, and avoid any useless, distracting character... That's my suggestion...

[COLOR="Blue"][SIZE="2"][FONT="Comic Sans MS"]Sorry butI did it to get some attention to my request. Becouse after 5 days of "normally" posted thread there wasnt any suggestions at all. 

I hope u understand me :) 

**koenn**

I found this one but when I click *SAVE* (modified file) I get this message:

**Cant open file to write** - what this supposed to mean? And I cant change files permissions[/FONT][/SIZE][/COLOR]

---

### Post by darrenm on 2007-03-04
Your network card is a very generic one, probably one of the most common network controller chipsets in the world. Ubuntu should just support this fine.

Cable username and password are stored in the cable modem/router, not the network card so as long as you configure your network card then you should be fine.

To write to the file try this from the terminal:
```
sudo gedit /etc/modules
``` then add rtl8139 to the end.

---

### Post by cannabis on 2007-03-04
> **darrenm said:**
> Your network card is a very generic one, probably one of the most common network controller chipsets in the world. Ubuntu should just support this fine.

Cable username and password are stored in the cable modem/router, not the network card so as long as you configure your network card then you should be fine.

To write to the file try this from the terminal:
```
sudo gedit /etc/modules
``` then add rtl8139 to the end.

[FONT="Comic Sans MS"][SIZE="2"][COLOR="Blue"]here is screenshot about what I get when typing this command

```
sudo gedit /etc/modules
```

[ [IMG]http://www.imagehosting.com/out.php/t295701_DSC04376.gif[/IMG]](http://www.imagehosting.com/out.php/i295701_DSC04376.gif)[/COLOR][/SIZE][/FONT]

---

### Post by darrenm on 2007-03-04
Ah sorry you're on xfce. Use nano then

```
sudo nano /etc/modules
```

---

### Post by cannabis on 2007-03-04
> **darrenm said:**
> Ah sorry you're on xfce. Use nano then

```
sudo nano /etc/modules
```


[COLOR="Blue"][SIZE="2"][FONT="Comic Sans MS"]Hey!

Now I have added this function to **/etc/modules** and rebooted but .... what I should do now? There is just MODEM option in [COLOR="SeaGreen"]Network COnfiguration[/COLOR]

[ [IMG]http://www.imagehosting.com/out.php/t296120_DSC04377.gif[/IMG]](http://www.imagehosting.com/out.php/i296120_DSC04377.gif)

**Thanx!**


P.S. I always setuped drivers on Windows system to get my Network Card work ...[/FONT][/SIZE][/COLOR]

---

### Post by chili555 on 2007-03-04
Please try sudo modprobe 8139too and see if that kicks it to life. If so, you want to change the modules file to 8139too instead of rt8139.

---

