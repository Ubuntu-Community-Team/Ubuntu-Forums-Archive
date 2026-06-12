---
title: "double-click script/launcher, keep terminal open"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by worldsayshi on 2009-11-24
I have an executable script: /home/myself/scripts/dostuff

I have confirmed that running ./dostuff or 'sh dostuff' runs the script correctly.

Now I want to place a launcher for the script on the desktop. I create a launcher with the command 'sh /home/myself/scripts/dostuff', and set it to run in a terminal and I add 'read' to the end of my script.

However, when I run (by double-clicking on it) the script, the terminal doesn't stay up. It just flashes for a split nanosecond. What am I doing wrong?

---

### Post by pi4r0n on 2009-11-24
Show us the code first; so we can see what it does.

Cheers

pi4r0n

---

### Post by worldsayshi on 2009-11-24
ok.

```
dt="`date +den_%y%m%d.kl_%H:%M:%S`"
echo "creating backup: $dt"
tar -cf backup/"$dt" *.odt *.ods
read
```

It's a very simple backup script, archiving all ods and odt documents in  tar-files with date stamps, from the folder it runs from. What's it doesn't do when I run it from a launcher is staying up so I can read if there are any errors. I've had similar problems before...

---

### Post by bodhi.zazen on 2009-11-24
You have to call the script to run in a terminal.

Most terminals use -e , so ...

```
xterm -e "/path/to/your_script"
```

---

### Post by kaibob on 2009-11-24
I have an alternate suggestion. It runs the script from a desktop launcher and leaves the terminal window open. I removed the read command from your script and used bash. 

```
gnome-terminal --execute bash -c "/path/scriptname ; bash"
```

---

### Post by worldsayshi on 2009-11-27
> **kaibob said:**
> I have an alternate suggestion. It runs the script from a desktop launcher and leaves the terminal window open. I removed the read command from your script and used bash. 

```
gnome-terminal --execute bash -c "/path/scriptname ; bash"
```

Yes, that surely worked. I would have to include going to the folder that I wanted to make the backup from first though, since the script doesn't have absolute paths (in case anyone tries to reproduce).

It's a bit strange that "run in terminal" doesn't work though. Shouldn't that do the same thing (running the script in the gnome-terminal)?

---

### Post by SuperNatendo on 2009-12-03
Thank You so much!

This has helped me make it easier for my coworkers (mostly windoze techies) to run the clonezilla server I set up for us to use!

Clonezilla needs the terminal that launched it to stay open for the multicast clients to be able to start properly.

I made a script called 'clonezilla.sh'

```
sudo /opt/drbl/sbin/dcs
```

and a launcher with the following command:

```
gnome-terminal --execute bash -c "/path/to/clonezilla.sh ; bash"
```

---

