---
title: "How do i run deluge from terminal?"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Rigorous on 2009-08-10
Hi, I want to know the command to run deluge from terminal because I want to run it at a certain time using scheduled tasks.

Thanks!

---

### Post by t0p on 2009-08-10
I don't use deluge.  But I can tell you that the usual way to run a program from the terminal is simply to type in the program's name.  So I suggest you try typing into the terminal:

```
deluge
```

---

### Post by Yvan300 on 2009-08-10
Deluge is a gui torrenting app as far as i know, if u want a terminal torrent client, then use transmission.

---

### Post by Rigorous on 2009-08-10
Yes deluge is a gui torrent app, I'm using it because transmission would only allow a maximum of 50 connections and I would change it to 200 or w/e and it would never connect to more than 50. Also, thanks t0p.

---

### Post by Christmas on 2009-08-10
Here's a Perl script which may do what you want. Just make it executable (**chmod 755 schedule.pl**) and then run it as **./schedule.pl**. When it is ran, it will ask you for the number of seconds in which you want Deluge to be ran (I know, this could've been done more fancier but hope it helps).
```
#!/usr/bin/perl

print "In how many seconds should I run the application? ";
my $time_run = <STDIN>; # number of seconds in which the program should run
chomp ($time_run);
print "Running application in $time_run seconds.\n";
my $time_init = `date +"%s"`;
while (1)
{
    my $time_now = `date +"%s"`;
    my $time_diff = $time_now - $time_init;
    if ($time_diff == $time_run)
    {
	system ("deluge");
    }
}
```

Alternately, you can use:
```
 sleep <NUMBER_OF_SECONDS>; deluge
```

---

### Post by TheForumTroll on 2009-08-10
Deluge has more than one UI. It has Gtk, web and console. You can also run it as a daemon (deluged) and then use a GUI on another computer to connect to it.

```

deluge --ui=console

```

Have a look at 'man deluge' ('man deluged' and the [Deluged FAQ]("http://dev.deluge-torrent.org/wiki/Faq#Daemon") if you want to run it as a daemon).

---

### Post by colau on 2009-08-17
> **Rigorous said:**
> Hi, I want to know the command to run deluge from terminal because I want to run it at a certain time using scheduled tasks.

Thanks!
```

deluge

```

---

