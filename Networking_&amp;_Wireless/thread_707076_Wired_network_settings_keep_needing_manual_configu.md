---
title: "Wired network settings keep needing manual configuration"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by AndrewMcNZ on 2008-02-25
Hi everyone

I have a broadband Internet connection at home and connect my machine running Ubuntu Feisty to it by ethernet cable. The network is "always on" - I don't have to do anything special to connect to it. This was working perfectly until recently.

What happens now is that before I can connect to the internet I have to:
1) click on the nm-applet, 
2) select  "Manual configuration..." (which is the only choice), 
3) select my previously saved Location (which I named "Wired broadband")
4) Click on the green tick to "Apply location as the current configuration",
5) Click on Close to exit nm-applet.

Once I have done this, I can connect to the Internet (Firefox, Pan).
But, the nm-applet seems to "forget" the settings every few minutes or so (I haven't timed this) and I need to repeat the steps again. This is most noticeable in Firefox when I am frequently opening new links. Typically, I go to open a link in a new tab and the link is not found. If I then repeat the above steps and refresh the page, the page will load perfectly.

If the network was cutting off completely (for whatever reason) I might understand. But, if I have previously started a file download, or have a Youtube video streaming, then the download, or video, **continues uninterrupted** even though I cannot load any new web pages. When I redo the nm-applet steps, the downloading still continues without any hint of a problem.

Can anyone suggest anything I should try to solve this problem?
I am happy to supply further information if it is needed.

Cheers
Andrew

---

### Post by Sam Lars on 2008-02-25
Why are you closing it after you configure?

---

### Post by AndrewMcNZ on 2008-02-25
I am sorry, I was not as clear as I could have been. Step 5 should be:
5) Press Close to exit the "Network Settings" dialogue box.

The nm-applet is still present.

I close the dialogue box simply because I have finished using it to change the settings, and so that I can see my web browser in the background. I suppose that I could leave "Network Settings" open and see if it makes any difference. I expected that the settings would remain in effect even when the Network Settings dialogue is closed, but they do not.

Cheers,
Andrew

---

### Post by Sam Lars on 2008-02-25
Oh, yes, sorry, I thought you meant you closed the whole program... closing the dialog should be fine, since it seems to still work after that.
Have you tried configuring without nm-applet?

---

### Post by AndrewMcNZ on 2008-02-26
No, I haven't.
How would I go about that?

Cheers,
Andrew

---

### Post by Sam Lars on 2008-02-26
Through System > Administration > Network

---

### Post by stream303 on 2008-02-26
In some cases I have found Network Manager a problem.  If you are on a permanently wired network like I am at home, I have no need for it.

You may want to disable it.  My computer doesn't "roam" very much. :)

To disable it, (don't just remove it!), you need to just create two text files with the word "exit" in them.  Check this out:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

For me, I have no need of network manager.  This might not fix your problem, but it is easy to implement.

---

### Post by AndrewMcNZ on 2008-02-28
My network connection is now working \\:D/ without problems since I have disabled Network Manager.
To do this, I followed the instructions at the link that **stream303** gave: 
[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5]("https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5")

I ran the first two commands to stop Network Manager and wasn't quite sure what to expect. What happened was that the Network Manager applet disappeared from the panel at the top of the screen. I was then pleasantly surprised to find that my wired network had connection continued working during this process.

I then created the two text files listed in the instructions. I had to use sudo to get permission to create the files in the /etc/default/ folder.
To create the first file, I used:
```
sudo gedit /etc/default/NetworkManager
```

To create the second file, I used:
```
sudo gedit /etc/default/NetworkManagerDispatcher
```

After a restart (I could have just logged out and logged back in), the wired network connection is just working, and the Network Manager applet is nowhere to be seen.

I would say that this method (disabling Network Manager) fixes my problem, but is not really a long-term solution as I may want the convenience of Network manager in the future. Perhaps I will try using it again when Hardy (or perhaps Intrepid!) comes out.

Thank you to Sam Lars for your replies to my post, and especially to stream303 for directing me to the instructions.

Cheers
Andrew

---

