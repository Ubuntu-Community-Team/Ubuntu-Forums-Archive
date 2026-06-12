---
title: "Need help with zenity"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by micaparat on 2009-08-04
hi!
i'm trying to make a simple script of my own, just for fun. it's an autoshutdown script using zenity for the UI. does anyone know how to integrate a zenity progress dialog that shows the time remaining?
here is the piece of script:

```
#!/bin/bash          
MM="$(zenity --entry --title "In cate minute?" --text "In:" 10 15 20 30 45 60 120 )"
echo $MM
gksudo shutdown +$MM

```

i must add i'm an absolute beginner, i've read the manual for zenity, but didn't find much use in it for what i need.
thank you for your help!

---

### Post by bodhi.zazen on 2009-08-04
See if these  links help :

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

---

### Post by angry_johnnie on 2009-08-04
I don't believe (although, I must admit I'm really not sure) zenity will do what you want it to do.

It does have the ability to show progress.

It would go like this:

```
(
echo 30 ; sleep 1
echo "# blah blah blah blah..." ; sleep 1

some cool command

echo 60 ; sleep 1
echo "# more blah blah..." ; sleep 1

some other cool command

yet another cool command

echo 90 ; sleep 1
echo "# even more blah blah..." ; sleep 1

some more commands

echo 100 ; sleep 1

) | zenity --progress --pulsate --auto-close --auto-kill --title="Your Title" --text="blah blah blah..." --percentage=0 --width 350 --height 25
```


This would show progress:  starting at 0%, then moving really fast to 30%, and then gradually to 60%, 90% and 100%.

But then the tricky part is the echo command, which is telling zenity just how much progress to show.  And, it only echoes in between commands.

In this case, you're trying to send an echo, or progress signal for a single command.

So, I don't think it's possible.  But then again, I just may be wrong. :)

And, about the auto shutdown script, take a look at mine (attached).  See what you can make of it.  Use it.  Change it.  Do whatever.  That's why this is free --as in freedom and beer-- software.

:KS

---

### Post by micaparat on 2009-08-05
thank you for the tips, you guys are awesome! ill play around with the script, read a little more and see what i can do, i'll post it here when i have something interesting.
:KS:KS

---

### Post by VCoolio on 2009-08-05
Maybe [this]("http://www.gnome-look.org/content/show.php/Watcher+--+Zenity+Progress+Window?content=104818") can help.

---

### Post by micaparat on 2009-08-05
Thanks, VCoolio! I'll have to read a little more about bash scripting though, before i grasp the basics. I'm really new to programming.:) Thankyou!

---

