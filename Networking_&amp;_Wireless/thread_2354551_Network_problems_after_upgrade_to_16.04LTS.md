---
title: "Network problems after upgrade to 16.04LTS"
date: 2017-03-03
forum: Networking &amp; Wireless
---

### Post by WB0HYQ on 2017-03-03
My computer connected just fine before I upgraded to 16.04. Now, every start has something that fails and wants me to send the report (which I do). But my most frustrating thing is my networking.

If I open File Manager, I see all my own files. If I select "Network" I see "Windows Network". Double-clicking that icon produces absolutely nothing. I have checked samba.conf and made sure my WORKGROUP is correct (it is). Samba itself will not let me connect to anything because under the Network tab it says "No workgroups found". I have one workgroup and five computers in it running various flavors of Windows 7. Before I could connect fine. Now I can't.

The above is using Wireless connections.

Now, using a cabled connection I get the same results, but I am able to use Gigolo to manually enter a connection to my computers, asking for shared directories. I get them fine and can access them. I can access the Internet using either connection.

There is a warning (when I am in WiFi mode) that pops up in the upper right, lasting for around 3 seconds, that says something about my having a domain incompatible with xxxxxxx and has been stopped. (it flashes off so fast i can't read it) This is probably part of my problem. Anyone know what the incompatibility is?

Bill

---

### Post by WB0HYQ on 2017-03-10
Oh com on now! ONE view after SIX days? That's hard to believe. Is the forum that dead?

I can see by all the posts that networking for 16.04/.14 is badly implemented. Will that change in the future, or is it better to go back to 14.04?

Bill

---

### Post by QIII on 2017-03-10
Hello!

The number of views may not be even close to accurate.  We've had problems in the past where views have been zeroed out.

If you want better attention, I recommend bumping your post at 12 hours if you have not received a response.  In six days' time your thread had sunk to the bottom of the sea and was several feet deep in the sediment.  Nobody was likely to notice it.

---

### Post by WB0HYQ on 2017-03-10
True. that's where I found it. But, at the beginning, it remained on the top page for around 15 hours. That's neither here nor there at the moment. I still can't use my Ubuntu machine because of the network failure.

Bill

---

### Post by WB0HYQ on 2017-03-11
No matter, now. It has been solved in another thread.

Entering: host -t SOA local 8.8.8.8

Fixed the problem. I can now browse all my Windows machines shared directories just fine. This setting will survive a reboot also. I don't know what it does, exactly, but it works.

Bill

---

