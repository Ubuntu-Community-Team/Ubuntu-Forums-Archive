---
title: "Help running script on gedit!"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by hasan1 on 2009-12-05
Running Ubuntu for the first time.Ubuntu 9.10 live usb.
Gedit settings for running script!
Following are my screenshots I have also changed #!/bin/bash to #!/bin/sh
The build command gives an error and the run command opens another window!

[[IMG]http://img198.imageshack.us/img198/7646/buildv.th.png[/IMG]]("http://img198.imageshack.us/i/buildv.png/")

[[IMG]http://img193.imageshack.us/img193/8986/runu.th.png[/IMG]]("http://img193.imageshack.us/i/runu.png/")

[[IMG]http://img190.imageshack.us/img190/7730/manageexternaltoolsruns.th.png[/IMG]]("http://img190.imageshack.us/i/manageexternaltoolsruns.png/")

[[IMG]http://img707.imageshack.us/img707/3177/manageexternaltoolsbuil.th.png[/IMG]]("http://img707.imageshack.us/i/manageexternaltoolsbuil.png/")

---

### Post by whitethorn on 2009-12-05
That definately doesn't look like bash. I would probably write your program like this

Save the program as test
> 
#!/bin/bash
for i in `seq 1 9`;
do
      echo $i
done

You should run the following commands in the terminal found in Applications -> Accessories -> Terminal.

You then need to add execute permission to the file (also possible by right clicking on the file, then permissions tab and ticking allow executing file as program) .   

```
chmod +x test
```

then execute the program, you should do this in the terminal

```
./test
```

What you wrote looks a like c++ in which case you'd need different headers, and you'd need to compile it using gcc or g++ and then run the program. In order to figure out how to compile with gcc read the man page. Once again in a terminal run.

```
man gcc
```

If you want to learn more about bash scripting.  There are a bunch of good sites out there althout I usually just use a cheat sheet like this one

[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

Oh and have a look at this site, [http://www.nixtutor.com/linux/all-the-best-linux-cheat-sheets/](http://www.nixtutor.com/linux/all-the-best-linux-cheat-sheets/)

---

### Post by hasan1 on 2009-12-06
[COLOR=Black]Thanks [/COLOR]_[whitethorn]("http://ubuntuforums.org/member.php?u=424805")_ for a quick reply.I will be doing **sh** scripting I think for simple scripts there is not much difference between **bash** and **sh**.

And that was a C code, now I know C and bash/sh have different syntax.I'll try it and hopefully it would run.

---

