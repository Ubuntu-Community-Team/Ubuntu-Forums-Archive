---
title: "xampp, starting the app with non-root privilege"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by woodsonoversoul on 2010-05-14
Hello all,
    I've trying to create a launcher to start xampp, but I need to be root to do so, is there any work-around to this? I know it's a needed security feature, but I'd really like to be able to start xampp from gnome-do or the main menu.

Thanks in advance,
Dan

---

### Post by -humanaut- on 2010-05-14
sudo chmod 777 /where/ever/fileis would escalate user privileges to execute the file.

---

### Post by woodsonoversoul on 2010-05-14
That won't mess up any of the underlying "server" stuff?

---

### Post by -humanaut- on 2010-05-14
Honestly, I'm not sure if it's a single-user system I can't imagine it would do much more then make it executable to your user but I'm no server expert.

---

