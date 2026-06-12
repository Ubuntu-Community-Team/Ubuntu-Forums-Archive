---
title: "bluetooth trouble"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by renjithforever on 2009-05-01
hello to all.... i am a newbie here...
and this is my first post.....

i am on intrepid .. i need help with my bluetooth, cant get it to work..the bluetooth Preferences says,adapter not found pls help.. :)

---

### Post by MontelEdwards on 2009-05-04
Hmm, let's try to resart the dongle.
Open a terminal by going to applications> accessories >terminal
and then type in ```
hcitool dev
``` this little command will list all of the Bluetooth adapters in the computer it will be something like > hci0    XX:XX:XX:XX:XX:XX


and then run ```
sudo hciconfig hci0 reset
```

cheers,
montel

---

### Post by Wazzag on 2009-05-05
Intrepid has multiple bluetooth problems
I could never get it to work until I upgraded to Jaunty

---

### Post by netwarriorwy on 2009-05-05
I had bluetooth problems at Hardy but after doing a fresh install on Intrepid I had no problems, everything worked fine.

---

