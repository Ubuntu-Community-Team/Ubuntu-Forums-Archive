---
title: "Unpriviledged user conncting to internet"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Helaya on 2009-03-09
Hello...
I am connecting to the internet by entering sudo wvdial connect at the terminal.(Through a wireless modem). but how can an unprivileged or desktop user who doesnt have administrative rights connect to the net. Any one to help me please. :(

---

### Post by sandyd on 2009-03-09
you can do this


its dangerous, but its the fastest way


how to remove the need to type in a sudo password

```

sudo visudo

```add this to the bottom (MODIFY IT FIRST!)(replace [username] with the username of the person, replace [path_to_app] with the path to the application)
P.S don't try chmodding the /etc/sudoers file
it will cause a kernel panic :) ( i tried it)

```

[username] ALL=NOPASSWD: [path_to_app]

```i would love to do the patch_to_app for you, but i have a wired, not wireless network so i have no idea what in the world that app is, or where it resides.

EDIT:
can you run this for me and post the output (one should have an error)
```

cat /usr/bin/wvdial
cat /usr/local/bin/wvdial

```

---

### Post by sandyd on 2009-03-09
the one without the error is [path to app]

P.S. try this :) Its a gui.... for wvdial
[http://linux.softpedia.com/get/System/Networking/pyWvDial-41078.shtml](http://linux.softpedia.com/get/System/Networking/pyWvDial-41078.shtml)

---

### Post by starcannon on 2009-03-09
Use your Users and Groups widget, no need to do dangerous sudo settings; here's a nice link with a step by step how to:
[http://www.vsubhash.com/writeups/ubuntu_linux_n_gnome_problemsolver.asp?how_to=Connect_To_Internet_Using_WvDial_Without_sudo_And_Password](http://www.vsubhash.com/writeups/ubuntu_linux_n_gnome_problemsolver.asp?how_to=Connect_To_Internet_Using_WvDial_Without_sudo_And_Password)

That oughta gitt'r dun.

GL

---

