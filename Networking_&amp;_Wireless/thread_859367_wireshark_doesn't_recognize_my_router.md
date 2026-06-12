---
title: "wireshark doesn't recognize my router"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by mattjack809 on 2008-07-14
wireshark does not recognize my router as an interface for capture. how can i fix this? :confused:

---

### Post by mattjack809 on 2008-07-15
ARGH!!!!! any answers???

---

### Post by jimv on 2008-07-15
I don't think you mean router, because a router is a little box separate from your computer.  You can't capture that.

---

### Post by hariprs on 2008-07-15
You can capture any packets that are coming/going out of your PC's NICs, if you are expecting to capture the packets that are coming from your router to your PC then you can capture it in your NIC.
You can also apply filter to capture only the packets that are coming from your router.

---

### Post by mattjack809 on 2008-07-15
yes i do mean router but thanks

---

### Post by mattjack809 on 2008-07-15
ohhh thanks let me see if it works

---

### Post by mattjack809 on 2008-07-16
eh... doesn't work. that wasn't really my question tho...

---

### Post by jimv on 2008-07-16
Perhaps if you explained in more detail what you're trying to do, then we can help you more.

---

### Post by PinkFloyd102489 on 2008-07-16
Just for clarification, WireShark will not see the router. Router is a separate box that puts out the wireless signal and chooses what data goes where.

A wireless card or ethernet card, which are both called NICs, are attached to the computer. They send and receive information based on the users input as to where they want to go or do.

---

