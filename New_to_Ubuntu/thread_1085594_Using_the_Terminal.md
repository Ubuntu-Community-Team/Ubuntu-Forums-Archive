---
title: "Using the Terminal"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by mistypotato on 2009-03-03
Hello :KS

What are the limitations on the LENGTH of the commands that can be typed into the terminal?

For example, I tried to type in a MonoRescue command string and it ended up being too long (so I'm now not sure how to run the command).


thx

---

### Post by Scunizi on 2009-03-03
My thought is that the mono rescue command is actually several commands stacked together.  if you see "&&" anywhere then that is the break point in the commands.  "&&" means "if the last command was successful continue with the following".  

As for the amount of text at one time on a terminal line.. I've no idea.

---

### Post by ilrudie on 2009-03-03
> **Scunizi said:**
> My thought is that the mono rescue command is actually several commands stacked together.  if you see "&&" anywhere then that is the break point in the commands.  "&&" means "if the last command was successful continue with the following".  

As for the amount of text at one time on a terminal line.. I've no idea.

A semicolon ";" can also separate commands.

---

### Post by halovivek on 2009-03-03
you can read more details about terminal [here]("http://linux.org.mt/article/terminal")

---

### Post by mistypotato on 2009-03-04
Thanks guys.

**[COLOR="DarkRed"]halovivek:[/COLOR]**
Thanks for the link, some very good info on the terminal, unfortunately, however, as happens a majority of the time, the SPECIFIC information I need at this time does not appear to be there.  That tutorial came close with the discussion on "scripts", however, as a Linux newbie, I don't think I'm wanting to execute a "series" of commands, but rather ONE LONG command with many "Parameters".   Now, even IF that part of the tutorial covers that, it was not clear to this particular newbie ;)

**[COLOR="DarkRed"]Scunizi & ilrudie[/COLOR]**
Thank you both for your time and response :KS

Newbie that I am, I am not sure your responses cover my original question?  I am not wanting to enter a set of commands to Terminal, Instead, it is ONE LONG COMMAND that has many parameters.  

When I try to enter and execut this one long command, it simply reprints the line on the screen with a ">" at I assume the point it no longer understands the command (because it's too long?)

So maybe your posts DO address how I enter this long command but I didn't "get it".  

Can I enter what is actually ONE LONG terminal command AS several different commands ?   Will MondoRescue correctly receive all the parameters even if it is broken up this way?

Pardon my "ignorance" on this....it's all new and I'm learning as quickly as possible and it is possible that the correct answer (solution) was given but that I am not realizing it :oops:


**[COLOR="SeaGreen"]Here's the actual command I'm trying to run.....(it's all on ONE line in Terminal (or supposed to be))[/COLOR]**
sudo mondoarchive -O -c -d /dev/scd0 -E /var/cache/mondo /dev/sda3/Mondotemp /dev/sda3  MondoScratch /mnt/cdrom /mnt/floppy /media /tmp /proc /sys /var/cache/mindi' -T /dev/sda3/Mondotemp  -s 4480 -S /dev/sda3/MondoScratch -F


thx again :KS:KS:KS

---

### Post by Big_Croc7 on 2009-03-04
Are you sure it isn't supposed to be:

sudo mondoarchive -O -c -d /dev/scd0 -E /var/cache/mondo /dev/sda3/Mondotemp **/dev/sda3/MondoScratch** /mnt/cdrom /mnt/floppy /media /tmp /proc /sys /var/cache/mindi' -T /dev/sda3/Mondotemp  -s 4480 -S /dev/sda3/MondoScratch -F

?

---

### Post by mistypotato on 2009-03-04
Hello BC,

Could be.

But I wasn't really concerned with the symantics of the line because it was just an example...not really a ready to use command string that is.  Allthough in YOUR string, it appears you DID add the Mondo scratch to the list of places NOT to be included which is a good thing.

The real issue is how to execute that line with terminal (or otherise) because it's sooooooooo  long

:P

---

### Post by kanikilu on 2009-03-04
What's the error you're getting?

I don't know if there is a limit to the length of a command, but you can split it over multiple lines with '\'. For example:

```
$ cd \[enter]
>/var\[enter]
>/log\[enter]
>/apt[enter]
```

Is the same as:

```
$ cd /var/log/apt
```

...not very practical for my example, but works well with long commands like what you are trying to do...

---

### Post by mistypotato on 2009-03-04
Hi kanikilu,

THAT'S the kind of info I was looking for. :KS:KS:KS:KS:KS

A way to actually enter and execute this long of a command string in Terminal.


I'll try that!  :D

Thanks

---

### Post by mistypotato on 2009-03-04
hmmmmm....


When I hit "enter" to begin the next line, it asks me for my sudo password and then executes what I typed in the first line?

How do I tell it NOT to execute the line until ALL lines have been typed in?

Also,....what if the line ENDS in the "/" character already?  Do I double them up?

If I create the line in a text editor first and paste it into the Terminal, THEN it takes the entire line and all "appears" well, but when I hit enter, it just goes to the NEXT line and puts a ">" at the beginning and then the cursor just sits there whee I would normally expect to see it ask for my password, but it doesn't.

---

### Post by davec64 on 2009-03-04
Just as an after thought, if you're planning on using the command again you could put it in a script and then execute it from the terminal as and when you want. :)

---

### Post by yther on 2009-03-04
> **Big_Croc7 said:**
> Are you sure it isn't supposed to be:

```
sudo mondoarchive -O -c -d /dev/scd0 -E /var/cache/mondo /dev/sda3/Mondotemp /dev/sda3/MondoScratch /mnt/cdrom /mnt/floppy /media /tmp /proc /sys /var/cache/mindi[COLOR="Red"]**'**[/COLOR] -T /dev/sda3/Mondotemp  -s 4480 -S /dev/sda3/MondoScratch -F
```

?

@mistypotato, you also have an unmatched quotation mark, which I put in red.  That will cause you to get the "OK, what next?" prompt, or >.  You should check to see if this is a stray bit of punctuation, or put its mate in somewhere, and then I think your command will work.  :)

---

### Post by mistypotato on 2009-03-04
IT WORKED  :guitar:


I'm IMPRESSED !!!  :KS:KS:KS:KS:KS



Thanks to your help, I now know how to do those REALLY long Mondo Archive command strings and hopefully others that search on this subject later will find this and it will help them too.

yther....taking the apostrophe out resolved that last issue  <YAY!>

---

### Post by kanikilu on 2009-03-05
> **mistypotato said:**
> Also,....what if the line ENDS in the **"/"** character already?  Do I double them up? I'm not sure if that is a typo or not, but it should be a backslash, --> **"\"** <--, like in my example. It should not ask you for your password until you press enter on the last line (with no backslash).

// Edit - oops, didn't read the last couple posts and didn't realize this was resolved. Sorry for resurrecting the dead ;)

---

