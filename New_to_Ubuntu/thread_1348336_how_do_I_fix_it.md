---
title: "how do I fix it???"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by freedomsearcher2442 on 2009-12-07
I installed adobe flash player but now I am gettiong an error  that says the download messed up and I cant open update manager so I have no idea how to fix this without reinstalling everything I tried to fix it thru terminal but I dont fully understand how to use the commands and such

---

### Post by wojox on 2009-12-07
Try this

```

#Remove Flash
# Deletes a troublesome config file
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
# Force-reconfigures adobe-flashplugin
sudo dpkg-reconfigure adobe-flashplugin --force
# Force-removes adobe-flashplugin
sudo dpkg --purge --force-all adobe-flashplugin
# Installs flashplayer the easy way
sudo apt-get install flashplugin-nonfree


```

---

### Post by freedomsearcher2442 on 2009-12-07
I hate sounding stupid but if you dont ask you dont learn where would I put that code?

---

### Post by rasmus91 on 2009-12-07
In your terminal...

---

### Post by freedomsearcher2442 on 2009-12-07
I understand that I asked wrong, I dont understand the code though how do i type it the whole thing? piece by piece and if so what pieces when I'm really new to this and havent used a dos like environment since I was probably 8

---

### Post by SwatKat on 2009-12-07
Go to Applications> Accessories> Terminal

```
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
```Copy the above line(whole), paste it in your terminal and hit enter. Type your password when prompted.

Then copy this line, paste it in the terminal and press enter

```
sudo dpkg-reconfigure adobe-flashplugin --force
```Repeat the process with the next 2 lines, one by one

```
sudo dpkg --purge --force-all adobe-flashplugin
``````
sudo apt-get install flashplugin-nonfree
```I borrowed the codes from wojox(Copy pasted it:)). I just told you how to enter it in your terminal, thats all.

---

### Post by hal10000 on 2009-12-07
> I hate sounding stupid but if you dont ask you dont learn where would I put that code?

All lines in posting 2 without a leading # are commands.
Try one or more of them, but first perform:
[code]sudo apt-get update[code]

---

### Post by freedomsearcher2442 on 2009-12-07
when i type in the first line this is what I get rm: cannot remove `/var/lib/dpkg/info/adobe-flashplugin.prerm': No such file or directory

---

### Post by freedomsearcher2442 on 2009-12-07
ok guys thanks alot i got it to work just ignored the first command and went from there

---

