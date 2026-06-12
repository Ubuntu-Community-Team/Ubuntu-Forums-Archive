---
title: "ethernet"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-05-30
what terminal code will turn on the ethernet send recieve ability??
9.10  My port works but not connecting..

---

### Post by cariboo on 2010-05-30
A lot more info would be helpful, what is the output of:

```
sudo lshw -C network
```

you should be able to see if the correct driver is loaded from the output of the above command, the command will also tell you what device number your nic has. In the same terminal type:

```
sudo dhclient eth0
```

substitute your device for the one in the example above, If everything is working correctly the second command should pick up an ip address.

---

