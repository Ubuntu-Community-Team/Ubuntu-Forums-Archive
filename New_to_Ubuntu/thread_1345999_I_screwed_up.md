---
title: "I screwed up"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Diametric on 2009-12-04
So, I was trying to change my "echo $PATH" from:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

to

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games/[B]home/me/bin

[/B]By following the:

```

```PATH=$PATH:/home/**yourusername**/bin
export PATH

So I could continue with my scripting lesson.  I followed the directions and didn't change /yourusername/ from the command line and now my PATH looks like this:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/yourusername/bin:/home/yourusername/bin:/home/yourusername/bin:/home/yourusername/bin:/home/dylan/bin

Yeah, yeah...I know...stupid mistake...that I repeated.  How do I get it back to where I need it to be?  The rmdir command isn't wokring...I'm guessing because the file is too long?  I tried and here is the print:

me@me:~$ rmdir /home/yourusername/bin:/home/yourusername/bin:/home/yourusername/bin:/home/yourusername/bin:/home/dylan/bin
rmdir: failed to remove `/home/yourusername/bin:/home/yourusername/bin:/home/yourusername/bin:/home/yourusername/bin:/home/dylan/bin': No such file or directory

Any help, please?  Feel free to crack on the mistake...it was dumb...I just might need a bit of hand holding as I'm new to this.

Cheers,
-Diametric

---

### Post by M!K3_$ on 2009-12-04
change your path again?

---

### Post by Diametric on 2009-12-04
I tried that which is why it now repeats the: /home/yourusername/bin in the path...it was from my attempts to correct it using the same command...I'm a little confused here.

---

### Post by Some Penguin on 2009-12-04
rmdir is for removing directories, not changing environmental variables.  Thankfully, it will by default refuse to remove non-empty directories.


export PATH=/what/you/want/the/path/to/be

---

### Post by blueridgedog on 2009-12-04
Your path will be reset when you reboot/log off in.  Not to worry.

---

### Post by Diametric on 2009-12-04
> **Some Penguin said:**
> rmdir is for removing directories, not changing environmental variables.  Thankfully, it will by default refuse to remove non-empty directories.


export PATH=/what/you/want/the/path/to/be

Nice...thanks Some Penguin...that was what I needed.  For what it's worth, rebooting did not change the path back to what it was.

---

### Post by apmcd47 on 2009-12-04
Assuming your shell is bash, add this to your .bashrc:

[PHP]vipath () 
{ 
    declare TFILE=/tmp/path.$LOGNAME.$$;
    echo $PATH | sed 's/^:/.:/;s/:$/:./' | sed 's/::/:.:/g' | tr ':' '\012' > $TFILE;
    vi $TFILE;
    PATH=`awk ' { if (NR>1) printf ":"
      printf "%s",$1 }' $TFILE`;
    rm -f $TFILE;
    echo $PATH
}
[/PHP]
If you prefer change the vi command to whatever editor you are comfortable with (screen-based, eg pico, rather than X-based) and rename vipath accordingly. Re-source your .bashrc and use this nifty PATH editor. Each directory in your path will be on a different line, making it easier to read and change your path. It won't change it for posterity, of course.

BTW the sed above removes the current directory from your path - always a security risk.

This is not my script, somebody passed it on to me. It may not have been his script, either.

Andrew

---

