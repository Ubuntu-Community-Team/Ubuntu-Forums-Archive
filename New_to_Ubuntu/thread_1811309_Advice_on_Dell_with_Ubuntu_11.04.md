---
title: "Advice on Dell with Ubuntu 11.04"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by Mr.Nutcase on 2011-07-24
I have a old Dell laptop that did not use in long long time..
It was running Windows XP sp3 
I installed Ubuntu 11.04 on it, its is great, makes the machine faster than before with XP. 
It is a Dell Latitude c400, it really old. Giving new life...
I installed VLC the media player.
Are any more media players can play other DVD
It can play some DVDs, but some are Region Lock or something.
It said it need file lib22 something
Also where is the menu for hooking VGA 15 to TV/monitor
thanks...

Oh I have backup windows XP, in my external hdd
I want to remove windows XP from the HDD on the internal Hdd.
Is there a way, I tried to delete windows in other computer by the dell hardrive hooked up 
to something like the one on the link...
[http://www.amazon.com/Sabrent-USB-DSC5-3-5-Inch-Converter-Adapter/dp/B000HJ99DI](http://www.amazon.com/Sabrent-USB-DSC5-3-5-Inch-Converter-Adapter/dp/B000HJ99DI)

---

### Post by Matt__ on 2011-07-24
for your dvd playback have you done this in the terminal?
```
sudo apt-get install libdvdread4

sudo /usr/share/doc/libdvdread4/install-css.sh
```enter one at a time, put in password when asked.

As for the WindowsXP partition, [open gparted](http://www.howtoforge.com/partitioning_with_gparted) (system/admin menu) and delete it, reformat the now free space to ext3 or ext4 (assuming you will be using only ubuntu on this machine, as windows operating systems cannot read ext3 or 4)

when its finished open a terminal
```
sudo update-grub
```what would be even better is reinstalling ubuntu from scratch using the whole HDD, making a partition for root, another for home directory and a 3rd for swap(equal to current RAM), or just let ubuntu do it automatically by telling it to use the entire disc.

[10 things to do after installing 11.04]("http://www.omgubuntu.co.uk/2011/04/10-things-to-do-after-installing-ubuntu-11-04/")

---

### Post by Mr.Nutcase on 2011-07-24
I could not find the : [[COLOR=#444444]open gparted[/COLOR]]("http://www.howtoforge.com/partitioning_with_gparted") (system/admin menu)
I guess I will have download it?
Is there a way to remove evething in the hard drive from another computer and still able to write on...
Anyway I bought 80gb hdd on ebay, On that one I will install virtual

---

