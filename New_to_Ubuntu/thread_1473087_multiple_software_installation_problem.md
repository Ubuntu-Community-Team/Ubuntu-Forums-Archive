---
title: "multiple software installation problem"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by henry cow on 2010-05-04
Help!

I keep wanting to try out software packages. I use Synaptic Package Manager and download whatever it offers me. Then I Apply, Install, or whatever else it tells me to do.

Later, I go back to Package Manager and see that the boxes in front of those packages are green and thus supposedly installed, but the actual programs are nowhere to be found.

Most recently I have tried to get Google Earth and Guayadeque. Do they have to be activated somehow or brought from the background into the actual Applications tab?

Where the heck are they? How can I use them?

My Ubuntu books are useless, they all say that it will automatically turn up in the menus and work.

thanks in advance

---

### Post by mechro on 2010-05-04
They won't always appear automatically in the Menus.

If it's a command line application it generally won't appear in the Menu.

Sometimes you have to Log out/Log in or reboot.

You may have to make your own Launcher for the application.

Having said all that try the following...

Right click the Menu Bar and select **Edit Menus**. You may find the application is somewhere in the Menus but needs enabling.

In Synaptic, right click the application, select Properties and look at the at the list of Installed Files. The command to start the application will usually be listed in the /usr/bin directory so you can start the application from a Terminal or Alt+F2 by typing **/usr/bin/*yourapplication***. You can create a Launcher using this command.

---

### Post by anonbeat on 2010-05-05
> **henry cow said:**
> Help!

I keep wanting to try out software packages. I use Synaptic Package Manager and download whatever it offers me. Then I Apply, Install, or whatever else it tells me to do.

Later, I go back to Package Manager and see that the boxes in front of those packages are green and thus supposedly installed, but the actual programs are nowhere to be found.

Most recently I have tried to get Google Earth and Guayadeque. Do they have to be activated somehow or brought from the background into the actual Applications tab?

Where the heck are they? How can I use them?

My Ubuntu books are useless, they all say that it will automatically turn up in the menus and work.

thanks in advance

To install guayadeque the easiest way to do it is to use the programmer repository as its not in the official repositories yet. Use this
```
add-apt-repository ppa:anonbeat/guayadeque
sudo apt-get update
sudo apt-get install guayadeque-svn
```

Greets

---

