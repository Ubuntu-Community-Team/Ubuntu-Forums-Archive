---
title: "can´t start it"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by scrin on 2010-07-28
hi i´ve just installed ubuntu netbook edition from this page and i seem to have a problem.

The installation went smoothly but when i try to enter the os all that i see is a black screen with a "_", 
well, i left it like that for several hours (went to play a videogame;)) and when i returned it had finally entered ubuntu.

After that i tried to se how much time it takes and....well i gave in after 1hr , its crazy please somebody help!!!!

---

### Post by an0dos on 2010-07-28
> **scrin said:**
> hi i´ve just installed ubuntu netbook edition from this page and i seem to have a problem.

The installation went smoothly but when i try to enter the os all that i see is a black screen with a "_", 
well, i left it like that for several hours (went to play a videogame;)) and when i returned it had finally entered ubuntu.

After that i tried to se how much time it takes and....well i gave in after 1hr , its crazy please somebody help!!!!

What are the specs of the computer?
What type of install did you do? (wubi?)

---

### Post by scrin on 2010-07-28
> **an0dos said:**
> What are the specs of the computer?
What type of install did you do? (wubi?)

i did exactly what says here:
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

about the netbook  it´s this exact model:
[IMG]http://www.print-insumos.com.ar/publicaciones/2010/Notebooks/HP/compaq_mini_cq10_120la/02.jpg[/IMG]
sorry about the size I don´t know how to change it....

---

### Post by an0dos on 2010-07-29
> **scrin said:**
> i did exactly what says here:
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

about the netbook  it´s this exact model:
[IMG]http://www.print-insumos.com.ar/publicaciones/2010/Notebooks/HP/compaq_mini_cq10_120la/02.jpg[/IMG]
sorry about the size I don´t know how to change it....

First you should check for available updates through the update manager or press alt-f2 and run the following command
```
Sudo apt-get update
```
Then press alt-F2 and run this command
```
Sudo apt-get upgrade
``` 


If that doesn't fix he problem open up the terminal and do the following:

```
Sudo apt-get install bootchart
```

Reboot

```
cd /var/log/bootchart; ls
```

You should see what package/program is causing it to boot slowly.

File a bug

```
ubuntu-bug pkg
```

You will likely be directed to a bug that has already been filed and may have a solution posted online.

---

### Post by an0dos on 2010-07-29
You may want to check to see if there is a bios option to change the sata controller mode to compatiblity.

---

### Post by stinkeye on 2010-07-29
Just a typo with capital "S" for sudo in your previous post that the OP
might stumble on. ):P
I do it a lot 'cause in my mind I'm starting a sentence.

---

### Post by an0dos on 2010-07-29
> **stinkeye said:**
> Just a typo with capital "S" for sudo in your previous post that the OP
might stumble on. ):P
I do it a lot 'cause in my mind I'm starting a sentence.

It's due to the automatic error correction in the stupid I-thingy that I used to type that response in.

---

### Post by scrin on 2010-07-30
it´s solved, all i had to do was deleting quiet splash and adding irqpoll like [Rybandt]("http://ubuntuforums.org/member.php?u=1104026") here:

**[http://ubuntuforums.org/showthread.php?t=1520772&highlight=quiet+splash](http://ubuntuforums.org/showthread.php?t=1520772&highlight=quiet+splash)**


(yet i dont understand how to make the change permanent)

---

