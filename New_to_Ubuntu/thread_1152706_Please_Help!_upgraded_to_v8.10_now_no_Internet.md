---
title: "Please Help! upgraded to v8.10 now no Internet"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by bobmac on 2009-05-08
Folks,

Using the upgrade option from the menu, I upgraded from v8.04 to v8.10. After the upgrade everything appeared to work OK except the fact that I now have no Internet connection.

I'm pretty well a novice so I followed all the prompts as best I could and believe that I got them all correct for my system.

I wonder if anyone can give me a clue (in a step by step way) as to how to fix this.

I've done a previous upgrade from v7.x to 8.04 with no problem and belive that I followed the same steps from 8.04 to v8.10.

Along the way I have installed all of the updates that have been sent.

Regards,

Bob

---

### Post by Peter09 on 2009-05-08
Can you post the output of the terminal commands

```
ifconfig
```
and
```
lshw -C network
```

also

check there is no hardware driver waiting to be enabled in System->Admin->Hardware Drivers

also

Is this just wireless or wired as well?

also - by adding > 'filename of your choice' to the above commands allows you to put the output in a file. So
```
ifconfig > text.txt
```
will give you a file with the output in it. Just in case you have difficulty in getting it posted.

---

### Post by bobmac on 2009-05-08
Peter,

Many thanks for your response, I've copied what you asked into the attachment.

Bob

---

### Post by Peter09 on 2009-05-08
Hi,
you appear to have two connections attached and running - this will not help. Stop one of them. Can you show the output of the command

```
route
```

---

### Post by bobmac on 2009-05-08
Peter,

My route command displayed as in the attachment.

Bob

---

### Post by Peter09 on 2009-05-08
Is home.gateway your router?

Do you get a response from the command

```
ping home.gateway
```

---

