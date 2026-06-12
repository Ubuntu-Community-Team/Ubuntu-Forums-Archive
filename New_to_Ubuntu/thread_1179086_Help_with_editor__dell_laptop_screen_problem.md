---
title: "Help with editor / dell laptop screen problem"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by benottendvm on 2009-06-05
I have a dell inspiron 8000.  (ati video card) 

just did clean install of  U 9.04 (without running from disk first - first mistake)

Now discovered split screen problem previously described many times.

found post by psyke83:  ubuntuforums.org/showthread.php?t=167670&highlight=Inspiron+8000

that sounds like will solve the exact problem.  BUT 

I don't know how to use the "editor"

where to find it ?

and how to "run" it.

especially since this is the only os that is running on this machine right now.

I think i can get the f7 command to work it in small screen.
and it runs fine when i load os in safe mode (ie video driver off)

i will gladly sit down this weekend and read the whole beginers manual.
BUT I really want to get machine working. (have a small point to prove to my wife)
and i think the reason this machine has been going belly up on me in past is windows
and i really don't want to go back there. 

thanks,
ben

---

### Post by verbal.kint on 2009-06-05
you can use any text editor to edit the file, gedit is probably the handiest.

so to edit the xorg.conf file with gedit you would type
```
gedit /etc/X11/xorg.conf
```

you may need to run it as superuser so you would type:
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by benottendvm on 2009-06-06
you can use any text editor to edit the file, gedit is probably the handiest.

so to edit the xorg.conf file with gedit you would type...

Ok I feel really stupid about this;

Where Do I find the Xorg.conf  file so i can edit it ????

thanks ,again

--ben

---

