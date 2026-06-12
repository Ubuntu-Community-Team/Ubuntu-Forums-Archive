---
title: "graphics problems"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by chazn85 on 2009-02-06
all,

after the latest kernel upgrade (23) my graphics drivers have stopped working.  Now ive tried to reinstall the correct drivers from the nvidia website, those being 64bit 8600GTS with no success.  The only way i can get a decent resolution is to boot into safe mode then init 3.  The exact point of failure at bootup is at rc.local but im sure this will come as now surprise.

Any help would be appreciated.

Thanks in advance

---

### Post by cariboo on 2009-02-06
How did you try to install the driver from Nvidia? There are specific steps you have to take to nstall the driver. First remove any Nvidia drivers you find listd in Synaptic. Make sure you have build-essential installed. Then press Ctrl-Alt-F1 to change to a console. Next at the prompt type:

```
sudo /etc/init.d/gdm stop
```

This will stop the X server. Now cd into the directory where the Nvidia binary is located then at the prompt type:

```
sudo chmod +x *run
```

The above command will make the binary file executeable. Now you can run the file, this assumes you only have one .run file in the directory:

```
sudo ./*run
```

answer yes to all the questions. When the driver has finished compiling at the prompt type:

```
sudo /etc/init.d/gdm start
```

this command will restart X and bring you back to your desktop with the new driver installed.

Jim

---

### Post by chazn85 on 2009-02-07
Thanks for your input.  Eventually i got it working via this method.  Seems like i had a mix and match of nvidia drivers which the update obviously didnt like :)

All good now thanks.

---

