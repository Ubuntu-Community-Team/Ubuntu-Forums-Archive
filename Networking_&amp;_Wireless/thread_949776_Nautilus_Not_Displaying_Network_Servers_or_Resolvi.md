---
title: "Nautilus Not Displaying Network Servers or Resolving Computer Names"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by simonfiction on 2008-10-16
Hi,
I've recently installed a fresh copy of Ubuntu for my dad to try out. The only problem is it seems to be having trouble seeing any machines on the network. If I go to "places->Network->etc" it doesn't display any machines at all. However, I ran the command "smbtree" and it showed my a full detailed list of all the machines on the network, with their names and their shares.

Secondly, I can't ping these machines by their names, but I can ping by IP address.

Thirdly, I can browse the shares directly if I enter IP address and share name, such as smb://192.168.1.102/music. But if I entered just the IP address (i.e. no share name attached) it won't display any of the shares available either.

I'm really struggling with this one as I've never had any issues with networking in Ubuntu before, it's always been straight forward. Any light shedding would be appreciated.

Also, a final note to say that from the windows machines I can browse the network fine, including any Ubuntu shares.

Adam

---

### Post by Iowan on 2008-10-16
I've notices similar things...
1. **smbtree** is, according to the **man** page:> A text based smb network browser which suggests it is designed to search out smb servers/shares. 
2. To ping by hostname, "something" must have a mapping of names-to-addresses.  This  could be a DNS server, or the **/etc/hosts** file. (also check out **man resolv.conf**). WINS is another naming option.
3. This is (or was) a (Nautilus?) bug - though I can't find a reference.

---

### Post by simonfiction on 2008-10-17
Thanks for the reply. Presumably though, if smbtree reports correctly, would this mean there is a problem with Nautilus? Does Nautilus network browser depend on smbtree?

Still no closer to solving my problem. Suprised this isn't a more common one. It's an incredibly basic network setup and a fresh ubuntu install.

---

### Post by sab0tage on 2008-10-17
Thought i'd add that i'm having same issue on my macbook, but shows up fine on my server - same ubuntu versions.

---

### Post by simonfiction on 2008-10-18
Cheers! Let you know if I get any closer to solving it.

---

### Post by robc02 on 2008-11-18
I seem to have the same problem. Nautilus is detecting my computer name incorrectly (ROB-HARDYDESKTO instead of ROB-HARDYDESKTOP). When I click on the icon Nautilus cannot find the shared folders. If I manually enter the correct location "smb://rob-hardydesktop" then Nautilus finds the shares OK.

pyNeighborhood behaves strangely, sometimes detecting the wrong name when run as root - this seems now to have corrected itself!

smbtree was finding the wrong name and then timing out, but is now finding the correct name and listing the shares. I am not aware of changing anything, all I have done is to open a few files to check their contents and closed without saving. Wierd

The question is - **where does Nautilus get the computer names from?** I strongly suspect that this will be the root of the problem.
I have checked /etc/hosts together with a few other possible places and the name is OK.

---

