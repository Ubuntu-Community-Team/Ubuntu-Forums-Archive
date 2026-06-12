---
title: "How to make a module permanent?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by kamssada on 2008-12-07
```

sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

```

this is my second day @ Kubuntu, i figured how to install the wirelless, but i need to apply these two modules to make it work... 

when i reinstall its all gone

i read somewhere i needed to copy it to /etc/modprobe.d/options, but how does that work, how do i do that?

i tried

```

sudo echo sudo modprobe ath_pci >> sudo /etc/modprobe.d/options
sudo echo sudo modprobe wlan_scan_sta >> sudo /etc/modprobe.d/options

```

or 

```

echo "ath_pci" sudo tee -a /etc/modprobe.d/options
echo "wlan_scan_sta" sudo tee -a /etc/modprobe.d/options

```

no success, is there something i am doing wrong... 

NB: this is my second day, will much appreciate if your response is not just theory... lol

---

### Post by madman92 on 2008-12-07
what you need to do is edit /etc/modules
append whatever modules you need to add at the end of the file
something like this:
```
sudo nano /etc/modules
```
then add the modules at the end of the file
then CTRL+x, then Y (yes to save), then it will exit
Hope this works for you

---

### Post by gettinoriginal on 2008-12-07
you need to edit the file to add it

sudo gedit /etc/modprobe.d/options

---

### Post by kamssada on 2008-12-07
> **madman92 said:**
> what you need to do is edit /etc/modules
append whatever modules you need to add at the end of the file
something like this:
```
sudo nano /etc/modules
```
then add the modules at the end of the file
then CTRL+x, then Y (yes to save), then it will exit
Hope this works for you

english please... so what you are saying is to sudo nano /ect/modules, that will create a new folder???

---

### Post by kamssada on 2008-12-07
> **gettinoriginal said:**
> you need to edit the file to add it

sudo gedit /etc/modprobe.d/options

i just copy the modprobe to the bottom of the file?

---

### Post by kamssada on 2008-12-07
i just copy the modprobe to the bottom of the file?

---

### Post by kamssada on 2008-12-07
english please???

---

### Post by kamssada on 2008-12-07
```
sudo gedit /etc/modprobe.d/options
[sudo] password for kenneth: [password entered]
sudo: gedit: command not found
```

i use kubuntu, by the ways

---

### Post by madman92 on 2008-12-07
nano is a terminal based text editor. If you do sudo nano /etc/modprobe.d/options it will open a buffer with the text from that file

---

### Post by kamssada on 2008-12-07
yeah i got that, i went in there... and typed my codes, but didn't work, it seems like i need to like call it from its folder or something...

---

