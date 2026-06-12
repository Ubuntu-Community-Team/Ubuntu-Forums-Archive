---
title: "launch terminal in a different directory"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by nl4m on 2010-02-23
Every time that I click on the gnome terminal it launches in the directory /home/user. Since I work from my desktop folder for the most part I want to change this. I want the gnome terminal to start in the directory /home/user/Desktop. How can I do this ?


I tried to change the value of the $HOME variable in hopes that the terminal will launch in the Desktop directory, it did not. I used "export", "readonly", and one other command to try to make the value of $HOME into an environmental variable but every time I restarted the terminal I'm back at /home/user.

---

### Post by patchwork on 2010-02-23
Create a custom keyboard shortcut with the following command:
```

gnome-terminal --working-directory=/home/<user>/Desktop

```Should do the trick

---

### Post by 2hot6ft2 on 2010-02-23
Install nautilus open terminal
```
sudo apt-get install nautilus-open-terminal
```
The use
```
sudo killall nautilus
```
now you have a right click option to "Open in Terminal" in whatever folder you're in. Including the Desktop

---

### Post by warp99 on 2010-02-23
You can also make the change permanent if you right mouse click on the applications menu then choose Edit Menus > Accessories > Terminal. Right mouse click and choose "properties". You can then add the code patchwork suggested in the command dialog box.

Another trick is if you install the package nautilus-open-terminal you can open a terminal in the current directory with a right click both on the desktop and in the file manager. This may be a better option since you only need to right click on the desktop to open a terminal in /home/<user>/Desktop.

---

### Post by nl4m on 2010-02-23
> **patchwork said:**
> Create a custom keyboard shortcut with the following command:
```

gnome-terminal --working-directory=/home/<user>/Desktop

```Should do the trick


Thanks a million. It worked like a charm.

---

### Post by n4h0j on 2010-03-26
> **patchwork said:**
> Create a custom keyboard shortcut with the following command:
```

gnome-terminal --working-directory=/home/<user>/Desktop

```Should do the trick

Thanks a lot, helped me out as well! =)

---

