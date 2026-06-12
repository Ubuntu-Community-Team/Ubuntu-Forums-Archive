---
title: "Administrator privledges"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by Canime on 2011-03-08
Hi there I want to use Wire shark network analyzer on my system, but it seems I need the right privilege. The reason I say this is because as I start it from the menu, and then go to change some of the options in the configuration panel, there are no interfaces to select. I looked on the net, and it seems I need to add admin privilege to it, in order for those devices to show up. Can I make it to start with the right access every time.

---

### Post by zenwalker on 2011-03-08
Add your user account to the root user group. That way youll get rights but i dont know if that will put your system at risk.

---

### Post by ubudog on 2011-03-08
If you can run it from the terminal, it would be something like this...

```
sudo wireshark
```

That will run it as root, or with Administrator Privileges.

PS: I'm not positive about that command, but you can always use sudo in a terminal to run things as root.  Also, note  that you won't be able to see your password, not even an asterisk or anything.  This is normal.

:-)

---

### Post by Canime on 2011-03-08
I really want to have the ability to load the program from the menu rather than having to open a terminal every time and typing sudo wire shark.

I have tried it, and it works from the terminal, but I don't want to change my account. I just want to add privilege to this one program so that it understands the devices on startup. Is there a utility that can add access controls to any of these programs in Linux?

---

### Post by mastablasta on 2011-03-08
you oculd create a launcher (shortcut) and in it put the command sudo wireshark.

---

### Post by dionysius on 2011-03-08
> **Canime said:**
> I really want to have the ability to load the program from the menu rather than having to open a terminal every time and typing sudo wire shark.

I have tried it, and it works from the terminal, but I don't want to change my account. I just want to add privilege to this one program so that it understands the devices on startup. Is there a utility that can add access controls to any of these programs in Linux?

To run Wireshark with privileges from the main menu, you should do the following:

1. Right-click on 'Applications' in the panel, and select 'Edit Menus'
2. Find Wireshark, select it, and then click on 'Properties' on the right
3. In the launcher properties, where it says 'command' type gksudo in front of wireshark
4. Close properties, close Edit Menus.

Now when you launch Wireshark from the menu it will ask you for your password and it will run as root.

---

