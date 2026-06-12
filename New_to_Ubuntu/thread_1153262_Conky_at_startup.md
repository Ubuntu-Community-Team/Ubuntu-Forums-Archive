---
title: "Conky at startup"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by Fernzaty on 2009-05-08
I can get Conky to run by hitting alt f2 to get a run box and typing in "conky". I would like it to automatically start at boot time so I created an entry in Preferences, Startup Applications, and again put the command "conky" in for the command, but it doesn't work. Can anyone please advise me?

---

### Post by divague on 2009-05-08
Open a text editor and copy this:

```
#!/bin/bash
sleep 20 &&
exec conky -d -c ~/.conkyrc &
exit
```

Save it with the extension .sh, for example conky_start.sh, and make it executable, then go to System->Preferences->Startup Applications and add the file you just created.

This file will start conky 20 seconds after the system loads.

Hope it helps.

---

### Post by slughappy1 on 2009-05-08
I would say you don't need it to be 20 seconds, but that is just your preference. After you make the text file, you must open a terminal and navigate to where your file is located and use the following command.
```
chmod +x file_name
```

Also, what is all that extra stuff for conky? I have never had to use any flags when loading. The .conkyrc seems a little redundant doesn't it? I mean conky automatically loads the ~/.conkyrc file.

---

### Post by americano70e10 on 2009-05-08
This is great! thnks guys, I was having the same problem!!!

---

### Post by blueridgedog on 2009-05-08
Alternatively, you could just put:

```
conky -d -c ~/.conkyrc
```

at the end of /etc/init.d/rc.local and have it start for all users...you will need to edit the file with

```
sudo gkedit /etc/init.d/rc.local
```

---

### Post by Fernzaty on 2009-05-09
Thanks for the help guys. I just created divague's script and stuck it in my root directory and it works just fine.

---

