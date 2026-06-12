---
title: "[SOLVED] Internet Connection with Livebox"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by Dumpy Dumpster on 2008-04-19
I have a livebox connected by ethernet cable to an XP machine and all works fine. I want to use a cable splitter to connect a second machine using Ubuntu 7.04, but only use one machine at a time. How can I get the software needed off the supplied CD as all the files do not open with Ubuntu?
__________________

---

### Post by jetsam on 2008-04-19
I'm not familiar with the livebox, but according to this [post]("http://www.orangeproblems.co.uk/phpBB2/viewtopic.php?p=27913") on their forums, you shouldn't need anything from the cd to set up a wired connection.  Try plugging in the Ubuntu computer and going to system-->administration-->network.  Then select the wired connection and hit properties.  Check "enable this connection" and set the dropdown menu to "automatic configuration (dhcp)".  Hit 'OK', and then make sure the wired connection is checked in the network settings window.  If all goes well, that should connect you.  

You almost certainly want a switch like [this]("http://www.amazon.com/NETGEAR-ProSafe-5-Port-Desktop-Switch/dp/B00002EQCW/ref=pd_bbs_1?ie=UTF8&s=electronics&qid=1208626762&sr=8-1") or [this]("http://www.amazon.com/NETGEAR-GS105-ProSafe-Gigabit-Ethernet/dp/B0000BVYT3/ref=pd_bbs_8?ie=UTF8&s=electronics&qid=1208626762&sr=8-8") and not a splitter.  You should, I think, then be able to use both computers simultaneously.   Those links are to Netgear switches.  I like them, but really any brand should be fine.

**Edited to add**: Just in case, don't buy directly from those links.  Find a source in France so you don't run into problems with power adapters.

---

### Post by Dumpy Dumpster on 2008-04-19
Thank you jetsam for your reply.
I did as you said,but the box to tick is 'Enable roaming connection' (there is no 'enable this connection' available) and there is no drop down box.  No blinding shaft of light!!!
Frustration levels are rising - just why does it not work!!
Splitter should be OK as only one machine will be connected at any one time.
Appreciate any more help - thanks again

---

### Post by jetsam on 2008-04-19
Right.  The interface is slightly different than I described.  I was using a modified Gutsy before.  Now I'm in my old Feisty 7.04 installation.  

You don't want roaming mode enabled.    You do want the configuration drop-down set to automatic configuration (dhcp.)  Hit ok, and be sure that the little box to the left of wired connection is checked in the window labeled Network Settings.  If you have a wireless card, uncheck it to simplify things for now.    

Hopefully that will work.  If it doesn't, open a terminal and try this command and post the text that comes out:
```
sudo /etc/init.d/networking restart
```

**Edited to add**: Also, have a look at this page [here]("http://help.orange.co.uk/documentDisplay.do?resultType=5002&docProp=$solution_id&groupId=1&directSolutionLink=3&gotoLink=0&page=&clusterName=DefaultCluster&docType=1006&docPropValue=kb14497").  There's an authentication step starting with step three.  I think you need to do this.

---

### Post by Dumpy Dumpster on 2008-04-20
Morning jetsam,
Here is 4.png
/home/michael/Desktop/Screenshot-michael@michael-desktop: ~-4.png
Make any sense to you?

---

### Post by jetsam on 2008-04-20
Good morning and evening.  I'm in California, so it's both. :)

I can't see your screenshot.  Can you repost it?  Use the attachment paper-clip on the top line of the editor menu to upload an image from your computer.   The image tag on the bottom line requires the image to be published on the web somewhere.

---

### Post by jetsam on 2008-04-20
I'm starting to think you may have a wiring problem related to the splitter.  See the image on this page:
[http://www.instructables.com/id/How-to-make-your-own-Ethernet-%22splitter%22/]("http://www.instructables.com/id/How-to-make-your-own-Ethernet-%22splitter%22/")

In order to use a splitter, you need two of them-- one on each end of the cable.  You'll then need to plug into both lan ports of your Livebox.  

I'm guessing you have one splitter attached to both computers and the other end of the cable attached to just one lan port of the Livebox.  This would mean the Ubuntu computer is attached to a dead cable.  

For testing purposes, you might want to unplug the working wiring from the XP computer and plug it into the Ubuntu machine.

---

