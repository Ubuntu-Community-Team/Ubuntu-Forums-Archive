---
title: "can't turn off computer"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by cartisdm on 2009-01-21
I'm running a pretty fresh install of mythbuntu 8.10.  I for some reason can't select   Applications --> Quit --> Shutdown

Once I select "Quit" nothing happens.  Just sits there.  The computer is working just fine but I have to use a terminal to reboot or shutdown my computer:confused:

---

### Post by 2hot6ft2 on 2009-01-21
Have you tried the "Magic Keys"? More info here. [http://www.acepcs.co.uk/index.php?a=knowbase&kbs=linux&kba=magickeys](http://www.acepcs.co.uk/index.php?a=knowbase&kbs=linux&kba=magickeys)> **cartisdm said:**
> I have to use a terminal to reboot or shutdown my computer:confused:Guess that doesn't help much.

---

### Post by cartisdm on 2009-01-21
If I have to use magic keys each time that'll be a real pain.  I'm using my computer as a HTPC so I don't generally have a keyboard out.  I simple use a mouse to close everything down when the time comes to shut everything down...

---

### Post by cmay on 2009-01-21
i am really sorry if i got this all or part wrong but i seem to remember having read in the forums a similar post where as it seems that a upgrade could fix it. it should have been due to a missing file in the upstream that the developers have forgotten. i am not sure however if it was jaunty jackalope or one of the regular ubuntu versions and i do hope i rember correctly also. i would hate to tell others something that is not true. can you maybe  try upgrading to fix the problem.  
good luck.

---

### Post by cartisdm on 2009-01-21
> **cmay said:**
> i am really sorry if i got this all or part wrong but i seem to remember having read in the forums a similar post where as it seems that a upgrade could fix it. it should have been due to a missing file in the upstream that the developers have forgotten. i am not sure however if it was jaunty jackalope or one of the regular ubuntu versions and i do hope i rember correctly also. i would hate to tell others something that is not true. can you maybe  try upgrading to fix the problem.  
good luck.

I'm running Intrepid now, and have the most recent updates.  Unfortunately, that didn't fix the problem (luckily though updates usually solve 95% of my other problems:))


EDIT:  Removed my quote of the spam post before

---

### Post by gjoellee on 2009-01-21
for shutdown:
```
sudo shutdown -h now
```

for more information:
```
man shutdown
```

---

### Post by 2hot6ft2 on 2009-01-21
Could be a broken package, you can try

```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
```
this will fix any packages. It's worth a shot.

Found this too.
> **kawaji said:**
> If you are using Compiz-Fusion, How about enabling Login/Logout plugin ?

Delete the default window matches and Enter the following line, for example.
```
class=Gnome-session & type=Dialog
```

Also, it would be better to add the above line into an entry box of "Above" window matches of Window Rule plugin.

---

