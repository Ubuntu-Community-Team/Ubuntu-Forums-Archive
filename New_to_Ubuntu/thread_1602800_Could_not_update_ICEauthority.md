---
title: "Could not update ICEauthority"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by Vege 4wd on 2010-10-21
Hi all, I am hoping someone can help with this problem.
After the last update every time after logging in I get this error message:

Could not update ICEauthority file/home/aaron/.Iceauthority.

Not a major problem but annoying.

Again any help would be appreciated.

---

### Post by A_M_S on 2010-10-21
Try this

[http://ubuntuforums.org/showthread.php?t=1061084](http://ubuntuforums.org/showthread.php?t=1061084)

---

### Post by Vege 4wd on 2010-10-22
Thanks I will give it a go tonight.:P

---

### Post by Vege 4wd on 2010-10-22
Hi I was able to work it out. As I am not too sure how to copy url I will paste answer here.

an 27, 2010
[Solved] Unable to update .ICEauthority error on booting

I received this error after installing updates and restarting the computer. It was nothing but a file-permission issue. You can easily fix it.

To solve it, type the follow these instructions:

Go to Application menu->Accessories->Terminal or press Alt+F2 and type gnome-terminal and press enter.

In terminal, type:

    sudo chown username:username .ICEauthority

    sudo chmod 0644 .ICEauthority

Replace username with your own username.

Restart your computer to check that the problem has been fixed.


Worked for me!

---

