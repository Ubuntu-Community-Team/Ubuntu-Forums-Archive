---
title: "devilspie installed but can not be opend"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by presieus on 2011-06-17
Hello

I am just new to ubuntu and today I tried to work with devilspie

I have it installed but every time I go to a terminal and type devilspie to start it,  I get the following message

nikolaus@ubuntu:~$ devilspie
No s-expressions loaded, quiting
nikolaus@ubuntu:~$ 

As far as I understand it, it means something is missing from the installation?

If anybody can help, greatly appreciated

---

### Post by Elfy on 2011-06-17
You need to have .ds files there for it to work with. 

[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

[http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/](http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/)

There's a gui for it - gdevilspie - [http://code.google.com/p/gdevilspie/](http://code.google.com/p/gdevilspie/)

Not sure if it works with the new version.

---

### Post by presieus on 2011-06-17
hello

Thanks for your replay.

I did download devilspie-0.22.tar.gz from the website and started to follow the instruction in the INSTALL file. 

When I did the ./configure I got the following error message

checking for WNCK... configure: error: Package requirements (glib-2.0 >= 2.9.1
        gdk-2.0
        libwnck-1.0 >= 0.17) were not met:

No package 'libwnck-1.0' found


In the Synaptic package manager I could not find libwnck-1.0, there are a bunch of other libwnck packages however.

Is there a way to install libwnck-1.0 differently? 

Furthermore, I did find the .ds files in the download as well,would there be a way to copy them into devilspie folder, and if so where would I find that?

Regards

---

### Post by Elfy on 2011-06-17
Is there a reason why you didn't just use the devilspie available from synaptic? I really think that you'd be better of using that - especially if the reason you downloaded devilspie is a rollover from using windows and needing to do so there.

Files in the repositories (available in software centre/synaptic and via apt-get or aptitude in a terminal) are tested to work with the version of ubuntu you are running.

You could copy the .ds files into the devilspie folder - it will be in you file manager (places) but it's called .devilspie - thus is normally hidden - Ctrl+H to show hidden folders.

---

### Post by presieus on 2011-06-17
I actually did installed it from synaptic first, that did not work however. 
It created the .devilspie folder but that was completely empty. I now paste the .ds files into it, would there be anything else I would have to do?

edit. I just run in a terminal devilspie -d to see if there is a problem

it returned this


nikolaus@ubuntu:~$ devilspie -d
Devil's Pie 0.22 starting...
Loading /etc/devilspie
/etc/devilspie doesn't exist
Loading /home/nikolaus/.devilspie
Loading /home/nikolaus/.devilspie/contains-true.ds
Loading /home/nikolaus/.devilspie/not-false.ds
Loading /home/nikolaus/.devilspie/not-true.ds
Loading /home/nikolaus/.devilspie/matches-true.ds
Loading /home/nikolaus/.devilspie/is-true.ds
Loading /home/nikolaus/.devilspie/matches-false.ds
Loading /home/nikolaus/.devilspie/literal-false.ds
Loading /home/nikolaus/.devilspie/literal-true.ds
Loading /home/nikolaus/.devilspie/contains-false.ds
Loading /home/nikolaus/.devilspie/is-false.ds
10 s-expressions loaded.
^C


This is the install from synaptic. If I understand it correctly the install did not create a folder in /etc. I did try to reinstall it already a few times.

---

### Post by Elfy on 2011-06-18
```
hobgoblin@hobgoblin:~$ devilspie -d
Devil's Pie 0.22 starting...
Loading /etc/devilspie
/etc/devilspie doesn't exist
Loading /home/hobgoblin/.devilspie
Loading /home/hobgoblin/.devilspie/clementine.ds
<snipped ...>
19 s-expressions loaded.
Changing workspace to 2
match
Changing workspace to 1
match

```

Works fine here and what yours reports looks ok.

What do your .ds files actually say, open one of them with gedit.

```
gedit /home/nikolaus/.devilspie/contains-true.ds
```

This is what my clementine.ds looks like - all I ask it to do is move it to another workspace.

```
; generated_rule clementine
( if 
( begin 
( is ( application_name ) "Clementine" )
) 
( begin 
( set_workspace 2 )
( println "match" )
)
)

```

If you run this what happens?

```
devilspie -a
```

I also have mine added to startup apps so it starts when the desktop does.

I've run it in xubuntu (from the repos) and from Fedora (from the repos) and had absolutely no issue with those versions.

---

### Post by presieus on 2011-06-18
Hello

Well Most of my .ds files are actually empty. 

for example 

```
gedit /home/nikolaus/.devilspie/contains-true.ds returns

```

returns 

```
nikolaus@ubuntu:~$ gedit home/nikolaus/.devilspie/contains-true.ds

(gedit:3481): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-SQ9Qcc1BbP,guid=04ebe9d6a2948feec201c5f00000038b failed: Failed to connect to socket /tmp/dbus-SQ9Qcc1BbP: Connection refused.
```


and the text file is empty.

I did installed clementine and tried your code, I get the following messages when I do devilspie -d

```
nikolaus@ubuntu:~$ devilspie -d
Devil's Pie 0.22 starting...
Loading /etc/devilspie
/etc/devilspie doesn't exist
Loading /home/nikolaus/.devilspie
Loading /home/nikolaus/.devilspie/contains-true.ds
Loading /home/nikolaus/.devilspie/not-false.ds
Loading /home/nikolaus/.devilspie/not-true.ds
Loading /home/nikolaus/.devilspie/matches-true.ds
Loading /home/nikolaus/.devilspie/is-true.ds
Loading /home/nikolaus/.devilspie/matches-false.ds
Loading /home/nikolaus/.devilspie/literal-false.ds
Loading /home/nikolaus/.devilspie/literal-true.ds
Loading /home/nikolaus/.devilspie/contains-false.ds
Loading /home/nikolaus/.devilspie/is-false.ds
Loading /home/nikolaus/.devilspie/clementine.ds
11 s-expressions loaded.

** (devilspie:3126): WARNING **: Workspace number 2 does not exist

(devilspie:3126): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed
Changing workspace to 2
match
```


when I do devilspie -a it gives

```
nikolaus@ubuntu:~$ devilspie -a

** (devilspie:3189): WARNING **: Workspace number 2 does not exist

(devilspie:3189): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed
match
```
 
I do have 4 workspaces however.

I installed ubuntu with wubi, is it possible something went wrong during installation?

Thanks

---

### Post by Elfy on 2011-06-18
No, I suspect it is down to workspace naming. Try renaimg your workspace 2 to Workspace 2.

Though I now have had another thought - if you're using the newest ubuntu with compiz then forget about devilspie and look into Workspace Rules for compiz.

If that's the case then I suggest another thread as this one will lead anyone else astray.

---

### Post by presieus on 2011-06-18
ok thanks, I do indeed have the latest version with compiz, I will look into it the workspace rules for compiz.

---

