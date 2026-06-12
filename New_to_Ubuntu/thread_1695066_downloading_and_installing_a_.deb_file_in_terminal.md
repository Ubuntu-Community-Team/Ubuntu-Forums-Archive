---
title: "downloading and installing a .deb file in terminal"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by Minanda on 2011-02-25
hey i have only been using ubuntu for a couple of weeks and im trying to download and install [http://www.shaplov.ru/files/sim/](http://www.shaplov.ru/files/sim/) using terminal. i attempted it yesterday while i had someone one hand to help and once downloaded it input cd/... and then was doing it step by step as i was told what to type but i missed the - in apt-get and had to start over, after which the cd/... command just kept bringing up no such file or directory, even though i was typing exactly the same thing, dont know why! anyway, i decided to delete the file and start from scratch but now i dont have someone on hand to help me step by step.

soooo, any help would be appreciated =)

---

### Post by Joe of loath on 2011-02-25
Find the URL of the file you want, and type
```
wget http://(your url here)
```

When it's finished, type

```
dpkg -i (file here)
```

That's all there is to it :D

---

### Post by Minanda on 2011-02-25
legend, thankyou. everything i found on google was making it look well complicated...probably clicking on random rubbish! =) cheers!

---

### Post by Minanda on 2011-02-25
ok i did that but it says, 'dpkg: requested operation requires superuser privilege'  :/

---

### Post by seawolf167 on 2011-02-25
Add a "sudo" in front of the command

```
sudo dpkg -i file.name.here
```

---

### Post by rburkartjo on 2011-02-25
min an easy way would be to install the deb file with the ubuntu software center. just click on the bottom of the deb file under properties and make it ex. then just open with the software center. i think it is easier. that is how i always install a deb file. your choice of course

---

### Post by Minanda on 2011-02-25
thanks! to both =)

yeah i know that but im trying to get used to using the terminal to do things, though =)

---

