---
title: "Compiz problem"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by acazosa on 2011-03-30
Hello, i had some problems with Ubuntu 10.10 . The computer was freezing very often so i decided to uninstall compiz packages. In fact was not a good idea :D when i restart the pc half of the screen was totaly black. So i reinstall all the compiz packages but the screen it s still half black. The problem it s that compiz doest start automatically when i log in. I create a startup application to run compiz at the start, now the screen it s ok but i still have some problem with some windows. Any guess?
thank you in advance

---

### Post by friv_livs on 2011-03-30
ATI or nvidia graphics card?

Try disabling desktop effects from the preferences->appearance menu.

---

### Post by acazosa on 2011-03-30
The desktop effect are already disabled. The problem it s that compiz doest run at the start unless i dont create a starup application

---

### Post by Dutch70 on 2011-03-30
Give this a try. You may want to write down or print the first couple steps, til you get back to the graphical environment.

1) After login, work in a tty (Control + Alt + F1). and remove the following

```
sudo aptitude remove compiz compiz-core
```

2) After that, install/reinstall the following

```
sudo apt-get install compiz compiz-core fusion-icon emerald simple-ccsm
```

3) Back to the graphic environment (Ctrl + Alt + F7) and run Compiz Fusion Icon (Apps >> System tools >> Compiz Fusion Icon)

4) The compiz fusion icon should appear in your panel. Right click >> Compiz options >> Indirect Rendering

5) Select Window Manager >> Compiz

6) To run Compiz fusion-icon at the start-up:

System >> Preferences >> Start up apps >> Add
Name: Compiz Fusion Icon
Command: fusion-icon -f
Comment: (optional)

7) Reboot

Please let us know if that works for you.

---

### Post by acazosa on 2011-03-31
So now it better. It s still freezing a little bit when i log in but for the rest seems all ok. Thank you very much for the support!

---

### Post by Dutch70 on 2011-03-31
Great! Do you mind telling us what you did to fix it, so others with the same problem will be able to try your solution? 

Also, what do you mean by "freezing a little bit"

---

