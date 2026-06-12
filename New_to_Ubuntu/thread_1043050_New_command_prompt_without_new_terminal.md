---
title: "New command prompt without new terminal"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Dirjel on 2009-01-18
How can I open a new command prompt after issuing a command such as "gnome-screensaver-command -i"?  Also, how can I end that process without closing the whole terminal?

Right now, the only way I know to use a command like that and still have access to that particular instance of the terminal is to use & at the end of the command, but I'm usually not thinking that far ahead >.>

---

### Post by bryncoles on 2009-01-18
i asked this question not so long ago! here's what i found out:

```
&		put this after a command in the terminal to allow the terminal to be used for other tasks.

^z		suspend a process, then
bg		background a process so you can do something else in the terminal
fg		foreground a process - bring it back
jobs		see what jobs are running
```

---

### Post by nothingspecial on 2009-01-18
```
sudo apt-get install screen
```

```
man screen
```

Screen let`s you have tabbed terminals or allows you to detach a process from a terminal, leaving it running while you do something else. I think it`s just what your looking for.

---

### Post by The Cog on 2009-01-18
I think I know what you mean. In your terminal, press Ctrl-Z, which freezes the process and makes the command terminal active agan. Then enter the command **bg** which puts the frozen process into the background, just as though it had been launched with **&**. You can see what processes are running in the background with the command **jobs**. You can even make it so they don't get killed when the terminal closes by using the command **disown**, which is described in **man bash**.

---

### Post by SteveDee on 2009-01-18
> **Dirjel said:**
> How can I open a new command prompt after issuing a command such as "gnome-screensaver-command -i"?  Also, how can I end that process without closing the whole terminal?

Right now, the only way I know to use a command like that and still have access to that particular instance of the terminal is to use & at the end of the command, but I'm usually not thinking that far ahead >.>

You can suspend a job with <crtl>Z

To cancel a running job you need the job number by typing; jobs

You can then kill a specific job; kill %1  {assuming its job number 1}

---

### Post by Dirjel on 2009-01-18
> **nothingspecial said:**
> ```
sudo apt-get install screen
```

```
man screen
```

Screen let`s you have tabbed terminals or allows you to detach a process from a terminal, leaving it running while you do something else. I think it`s just what your looking for.
I'm using Tilda, so I'm not sure if it's compatible.  I can already do tabs, but that's more hassle than what I want.
> **The Cog said:**
> I think I know what you mean. In your terminal, press Ctrl-Z, which freezes the process and makes the command terminal active agan. Then enter the command **bg** which puts the frozen process into the background, just as though it had been launched with **&**. You can see what processes are running in the background with the command **jobs**. You can even make it so they don't get killed when the terminal closes by using the command **disown**, which is described in **man bash**.
AHA.  This is what I needed.  Control Z it is.  Thanks to you too, brynocles.

> **SteveDee said:**
> You can suspend a job with <crtl>Z

To cancel a running job you need the job number by typing; jobs

You can then kill a specific job; kill %1  {assuming its job number 1}
This is handy as well.  I was using pidof (app name) then kill (the wonky number I got before).

Thanks, everyone!

---

