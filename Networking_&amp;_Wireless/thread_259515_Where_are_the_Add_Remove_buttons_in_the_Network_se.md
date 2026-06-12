---
title: "Where are the Add Remove buttons in the Network settings window?"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by bon_bkdfighter on 2006-09-17
Hi,
I'm a newbie. How can I make the Add / Remove buttons in the network settings window appear, so I can add / remove network devices??? In other words, I need to add network devices. How can I do that? Here's a screen shot of the window.
[IMG]http://photos1.blogger.com/blogger/4853/650/1600/Screenshot.png[/IMG]

If you can't see the pic, please go to this url: 

[http://photos1.blogger.com/blogger/4853/650/1600/Screenshot.png](http://photos1.blogger.com/blogger/4853/650/1600/Screenshot.png)

As you can see there is no add or remove button to add remove interfaces.


Thanks for any help in advance!!

bon

---

### Post by jd65pl on 2006-09-17
I believe that network devices should show if they are available.

Try

```
 lspci | grep {NETCARD NAME}
```

To see if it is enabled

e.g.

mine is a 3com wireless card so i put


```
 lspci | grep 3com
```

---

