---
title: "How to boot without starting apache2 by default??"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by antmenj on 2011-05-19
I have a lucid desktop i386 install.  I'v added apache to try serving locally behind a fire wall.  It works and thats all good but is there a way to only start apache manually?

This is primarily a desktop computer rather than a server and I don't want apache running by default all the time.

I know about these but thats only if its already going right?

sudo /etc/init.d/apache2 stop

sudo /etc/init.d/apache2 start

---

### Post by wildmanne39 on 2011-05-19
> **antmenj said:**
> I have a lucid desktop i386 install.  I'v added apache to try serving locally behind a fire wall.  It works and thats all good but is there a way to only start apache manually?

This is primarily a desktop computer rather than a server and I don't want apache running by default all the time.

I know about these but thats only if its already going right?

sudo /etc/init.d/apache2 stop

sudo /etc/init.d/apache2 start

Hi, go to start up apps and unchick it to start up.

---

### Post by lmarmisa on 2011-05-19
If you want to disable apache2 on startup, then type this command:

```

sudo update-rc.d -f apache2 remove

```

Then reboot your system. Apache2 will not be started automatically after the startup:

```

sudo service apache2 status

```

You can start manually apache2 typing:

```

sudo service apache2 start

```

Finally, if you wish to re-add apache2 to be started on boot up, type this other command:

```

sudo update-rc.d apache2 defaults

```

---

### Post by antmenj on 2011-05-19
> **lmarmisa said:**
> .......```

sudo update-rc.d -f apache2 remove

```............

Worked perfectly\\:D/  Thanks

---

### Post by lmarmisa on 2011-05-19
> **antmenj said:**
> Worked perfectly\\:D/  Thanks

Great!!!. 

Go to thread tools -> Mark this thread as SOLVED.

---

