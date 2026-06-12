---
title: "Installition"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by mbaybarsk on 2009-08-28
I need to install Packet Tracer 5.2. I have downloaded a ".bin" bile, which i can't get to work. How should i do that?

---

### Post by NoaHall on 2009-08-28
open a terminal, use cd to change to where you downloaded it to, then run ./filename.bin

So, for example -

cd /home/noah/Downloads
./myfile.bin

---

### Post by mbaybarsk on 2009-08-28
"baybars@Monster:~$ cd /home/baybars/desktop
bash: cd: /home/baybars/desktop: No such file or directory
baybars@Monster:~$ cd /home/baybars/Desktop
baybars@Monster:~/Desktop$ ./packettracer52.bin
bash: ./packettracer52.bin: Permission denied
baybars@Monster:~/Desktop$ "

What's wrong with this?

---

### Post by credobyte on 2009-08-28
```
sudo chmod +x filename.bin
```

Once you've executed this command, launch your .bin by double-click or via terminal ( check previous posts ).

---

### Post by mbaybarsk on 2009-08-28
Thanks NoaHall and credobyte! 

You have saved the day! And are my heroes :)

---

