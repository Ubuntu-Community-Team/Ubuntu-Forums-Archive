---
title: "[SOLVED] DWL-G122 Ver.:C1 With RT73"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by Hidetsu on 2008-02-19
I Finally got it done!
Been through Hard Work and lots of gooled...

Prepare your system. Open your terminal as root and verify if module-assistant is installed:

[CODE# dpkg -l module assistant[/CODE]

It should return something like this:

ii module-assistant 0.10.11 tool make module package creation easier

If you don't get that then install it:

```
# apt-get install module assistant
```

After that execute ths command:

```
# m-a prepare
```

Accept all so your system can be prepared.
Then when all is prepared, download the module:

```
# cd /
```

(To log into directory root)

Execute command to download the module:

```
# wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz
```

Now execute command:

```
# tar -vxzf rt73-cvs-daily.tar.gz
```

After that move the files to /usr/ directly to a new file wireless:

```
# mv rt73-cvs-2007092108 /usr/wireless
```
If by chance this is not the file you downloaded i have atached the file**

Now log into the wireless directory:

```
# cd /usr/wireless/
```

Read the "README" if you wish, it's allways good to take a look at it.

Now enter the directory Module:

```
# cd Module/
```

Now will start to install the module, execute the command:

```
# make
```

Wait a while, depending on the computer it should take a wihle.

If at the end this appear: 

make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.18-4-686'
*** Module rt73.ko built successfully

You are good to go! it means everything worked fine :)
If not review the steps again.

Keep on going and execute command:

```
# make install
```

If in the end this appear:

*** Install firmware in /lib/firmware ...
*** Check config ...

Everything went well and installed.

Congratulations Wlan0 is now installed with RT73 =D>

:biggrin::biggrin::biggrin::biggrin::biggrin::biggrin:
:lolflag:

---

### Post by Hidetsu on 2008-02-19
To See the Attached file you must be logged in.

I'll answer all the questions.

---

