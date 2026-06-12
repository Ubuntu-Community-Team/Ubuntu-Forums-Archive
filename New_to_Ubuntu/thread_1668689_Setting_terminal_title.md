---
title: "Setting terminal title"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by zzzonked on 2011-01-16
For now I'm using Terminal > Set Title > [new title]. Pretty straightforward. But I don't like the point-and-click.

I'm wondering if there's some command I can type in the terminal so I don't have to use the mouse for this? The reason is because I have a bunch of tabbed terminals each running a different program and I just want to title them so I know what's going on in each terminal. Thanks.

---

### Post by Smart Viking on 2011-01-16
read
```
man gnome-terminal
```

To launch with custom title:
```
gnome-terminal -t "your title"
```

---

### Post by Smart Viking on 2011-01-16
```
gnome-terminal -t "Your title"
```
read
```
man gnome-terminal
```

---

### Post by zzzonked on 2011-01-16
Thanks. But how do I set the title of the terminal tab I'm currently in? (I don't really want to open new windows. I'd rather keep all of them tabbed under the same window.)

---

### Post by DOSIX on 2011-01-16
i think it's under the terminal session dialog box somewhere. i don't remember where and i can't tell you right now because i'm not on linux i'm on windows since my ubuntu's internet isn't working.

---

### Post by zzzonked on 2011-01-16
I'm not looking for a dialog box point-and-click procedure. I'm looking for a quick

$ [command] -t [newtitle]

to change the title of the current terminal window/tab. Thanks.

---

### Post by Smart Viking on 2011-01-16
What do you need this for? If the whole point for this just is that you want a custom title on all of them you could just edit the launcher for gnome-terminal.

---

### Post by Clever_Username on 2011-01-16
If your using Putty you can use "wt". But I'm not sure about an xterm

---

### Post by Clever_Username on 2011-01-16
I also stumbled across [this]("http://www.unix.com/unix-dummies-questions-answers/35518-name-path-2.html") page that shows how to make the title of your xterm reflect your current directory. Hope it helps

---

### Post by Clever_Username on 2011-01-16
I also stumbled across [this]("http://www.unix.com/unix-dummies-questions-answers/35518-name-path-2.html") page that shows how to make the title of your xterm reflect your current directory. Hope it helps

---

### Post by zzzonked on 2011-01-16
> **Smart Viking said:**
> What do you need this for? If the whole point for this just is that you want a custom title on all of them you could just edit the launcher for gnome-terminal.
It seems no one understands what I'm looking for :( If I don't do this, then I have 15 terminal tabs open and all of them are titled "user@computer: [current directory]", which is stupid and completely useless when I need to find the right one. I want to launch firefox in one tab and rename that tab to "firefox"; launch emacs in another tab and rename that one to "emacs"; etc. Is this clear enough?

---

### Post by jpkotta on 2011-01-23
Put this in your ~/.bashrc (or use the echo line in a script).
```

function set_terminal_title()
{
    echo -ne "\033]0;$1\007"
}

```

Then you can set the title to whatever you want.
```
set_terminal_title "hello, world."
```

I like to do 
```
PROMPT_COMMAND='set_terminal_title "[${USER}@${HOSTNAME}][${PWD/$HOME/~}] "'
```

---

### Post by tbodine88 on 2011-09-02
> **jpkotta said:**
> Put this in your ~/.bashrc (or use the echo line in a script).
```

function set_terminal_title()
{
    echo -ne "\033]0;$1\007"
}

```Then you can set the title to whatever you want.
```
set_terminal_title "hello, world."
```I like to do 
```
PROMPT_COMMAND='set_terminal_title "[${USER}@${HOSTNAME}][${PWD/$HOME/~}] "'
```


This doesn't work on either Suse nor Unbuntu ub1104. It sort of works on Windows Command prompt, but the Command proccessor sets the title back. on Windows there is the "title" command to do this.

The above code does work for xterms, but not Gnome Terminal.

Regards Tom Bodine

---

### Post by cyber-monk on 2012-01-24
I think what your looking for is the **xtitle** command. I can confirm this works on the gnome terminal under Ubuntu 10.04. You can install it using:

```
$> sudo apt-get install xtitle
```

Once you have xtitle installed you can simply type:

```
$> xtitle your-new-title-here
```

The man page is online here:

[http://manpages.ubuntu.com/manpages/natty/man1/xtitle.1.html]("http://manpages.ubuntu.com/manpages/natty/man1/xtitle.1.html")

---

### Post by Zill on 2012-01-24
> **zzzonked said:**
> It seems no one understands what I'm looking for :( If I don't do this, [COLOR="Red"]then I have 15 terminal tabs open[/COLOR] and all of them are titled "user@computer: [current directory]", which is stupid and completely useless when I need to find the right one. I want to [COLOR="Red"]launch firefox in one tab and rename that tab to "firefox"[/COLOR]; launch emacs in another tab and rename that one to "emacs"; etc. Is this clear enough?
Do you *really* open 15 graphical apps (such as Firefox) from the terminal?  I understand the need to do this while debugging etc but, as a matter of routine, surely this is not necessary.  Just open them with a launcher in the usual way - fire and forget. ;-)

---

