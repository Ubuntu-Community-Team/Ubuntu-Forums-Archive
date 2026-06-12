---
title: "how to install new firefox"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by rahrahmah on 2009-08-20
I tried to learn how to install things once before with a less important piece of software, and failed. However, I can't keep using this OS if I can't figure out how to download and install anything. So, here I go again!

Firefox has been devouring all my CPU (I've tried flashblockers, no difference) and I've only just realized that I'm using an old version. 3.0somewhat, and there's a 3.5 out. I'm going to see if perhaps THAT helps a little (although I'm starting to think that firefox on ubuntu is just crappy :( ) 

Instead of fiddling with stuff then coming here, I'm going to come here first this time. So I downloaded the archive box thing (a .tar file?) I assume I extract it, but where to?

---

### Post by running_rabbit07 on 2009-08-20
Follow the instructions [here]("http://www.psychocats.net/ubuntu/firefox"), works every time.

Edit: if you use this technique, it will set up all of the links in your email and such to automatically use FF3.5 instead of being stuck copying and pasting to another browser every time you open something.

---

### Post by HotShotDJ on 2009-08-20
> **rahrahmah said:**
> I tried to learn how to install things once before with a less important piece of software, and failed. However, I can't keep using this OS if I can't figure out how to download and install anything.For many things, just use Applications --> Add/Remove.  Occasionally, you might need to use System --> Administration --> Synaptic Package Manager.  For Firefox 3.5, you'll need to use the second one.  Search for Firefox and then check off firefox-3.5.  It will be installed as a separate application under Applications --> Internet --> Shiretoko (the code name).  This allows it to be installed along side the Ubuntu supported Firefox 3.0.

Normally, you do not need to search the web and download software to install.  Most of what you need is handled using the above method.

---

### Post by mike555 on 2009-08-20
You should get Firefox 3.5 from the package manager -- that way it will be automatically be updated ............ it will install as "Shiretoko" in your menu .......

---

### Post by rahrahmah on 2009-08-20
"this allows it to be installed along side the Ubuntu supported Firefox 3.0."

Do I have to install alongside? Can't I just replace the old firefox? will 3.5 not work in ubuntu? I don't really want to have two versions of the same program if I don't have to, especially if one won't work very well/at all

---

### Post by running_rabbit07 on 2009-08-20
> **rahrahmah said:**
> "this allows it to be installed along side the Ubuntu supported Firefox 3.0."

Do I have to install alongside? Can't I just replace the old firefox? will 3.5 not work in ubuntu? I don't really want to have two versions of the same program if I don't have to, especially if one won't work very well/at all

Follow my the link up above and it will tell how to do it the best. All you have to do is download and save the FF3.5 file from the Mozilla site, then copy and paste one command. And yes, it does replace the old version. All of your shortcuts and the Icons in your email will automatically work with FF3.5.

---

### Post by rahrahmah on 2009-08-20
Sorry to be so full of questions, but I have [strike]one[/strike] several more before I do anything. I'm looking at the link you provided and they mention that most people wouldn't want to get the mozilla version and that only "some people" think it gives better performance. Do you think I am one of those people that would benifit?

I have a Pentium 4 2.93 Ghz and 370mb RAM. Which I just discovered is about 15mb of RAM under the recommended system reqs! is this a possible contribution to my high CPU usage and super laggy internet experiance?

---

### Post by sandyd on 2009-08-20
that is wayyy to little ram. add an extra 128mb stick and you **might** be happier

---

### Post by running_rabbit07 on 2009-08-20
> **rahrahmah said:**
> Sorry to be so full of questions, but I have [strike]one[/strike] several more before I do anything. I'm looking at the link you provided and they mention that most people wouldn't want to get the mozilla version and that only "some people" think it gives better performance. Do you think I am one of those people that would benifit?

I have a Pentium 4 2.93 Ghz and 370mb RAM. Which I just discovered is about 15mb of RAM under the recommended system reqs! is this a possible contribution to my high CPU usage and super laggy internet experiance?

As far as specs go, I am not sure. RAM may be a problem. As far as functionality, 3.5 seems just a bit faster and has the new tab button, other than that it is mostly the same as the old one.

It could be a number of things using up the CPU, such as Compiz. I found that installing Hardy uses much less CPU than Jaunty on my system but may not be the same for everyone.

---

### Post by running_rabbit07 on 2009-08-20
> **carlee said:**
> that is wayyy to little ram. add an extra 128mb stick and you **might** be happier

Do they sell RAM up there?

:lolflag:

Just kidding.

If running Xubuntu, that is plenty.

---

### Post by sandyd on 2009-08-20
Let me explain it a little clearer.
Ubuntu has a special partition in its hard drive. Its called swap. When you run out of ram, the system will use that as your RAM. your hard disk is signifigantely slower than your ram, which means that your whole system will be slow because it has to write / read from your hard drive.. The optimal solution is to have 2-3 gigs of ram, ive never seen ubuntu run over that. (unless im using a virtual machine)

---

### Post by sandyd on 2009-08-20
just do a reality check, i just pulled two pieces of ram from one of my computers thats lying around. now has one 256 and one 128. 

Tried firefox... and even though its a Intel Xeon dual core, its laggy. Definately not your processor's problem. 

time for a ram upgrade buddy.
or use Google chrome (although its plugins are kinda broken, v4 works quite fine and im typing from it right now)

---

### Post by running_rabbit07 on 2009-08-20
> **carlee said:**
>  (unless im using a virtual machine)

Even that depends on what you allow it to do. I gave Karmic 1 gig to use in VBox and I still don't break past 1.5 gigs with everything else running.

---

### Post by sandyd on 2009-08-20
even when running a machine, i don't bother to close anything on my desktop. so i already have a million programs running.. when the virtual machine is also running. programs account for about... 1.5GB, virtual machine accounts for 1-1.5GB.

There :)

---

### Post by sandyd on 2009-08-20
and it happens to be a dual quadcore xeon server im working on. except that one half of the server is donated to my website, while im using the rest.

---

### Post by mike555 on 2009-08-20
More RAM would help , and it's pretty cheap ........ check your "System" > "Administration" > "System Monitor" > Resources tab ......... if your swapfile is being used you should get more RAM ... check your motherboard specs to see max allowed -- many sites will do that for you ... (like .. [http://www.4allmemory.com](http://www.4allmemory.com) )  probably 2 GB ......

---

### Post by rahrahmah on 2009-08-20
Considering my Swap is always at least a little in use (which makes sense after what you explained it was, thanks for that I was confused!) I think we have a winner for firefox lag problems. I'm using ubuntu because it was free, so buying ram is out. Although, it's good to know what the problem is, at least. Thank you for that, too. I guess I won't bother replacing firefox especially since newer things tend to expect newer machines and I'm already in the weeds.

Did I hear mention that Xubuntu would run better on my machine? Should I send away for a CD?

---

### Post by mike555 on 2009-08-20
Xubuntu is only slightly lighter and not as good .........

---

### Post by running_rabbit07 on 2009-08-20
> **rahrahmah said:**
> Considering my Swap is always at least a little in use (which makes sense after what you explained it was, thanks for that I was confused!) I think we have a winner for firefox lag problems. I'm using ubuntu because it was free, so buying ram is out. Although, it's good to know what the problem is, at least. Thank you for that, too. I guess I won't bother replacing firefox especially since newer things tend to expect newer machines and I'm already in the weeds.

Did I hear mention that Xubuntu would run better on my machine? Should I send away for a CD?

I doesn't look as pretty, but it works excellant. I had it on an old laptop and it ran great. with 390MB RAM.

---

### Post by oldsoundguy on 2009-08-20
> **rahrahmah said:**
> Well, I'm using ubuntu because it was free, so buying ram is out. Although, it's good to know what the problem is, at least. Thank you. I guess I won't bother replacing firefox especially since newer things tend to expect newer machines and I'm already in the weeds.

Did I hear mention that Xubuntu would run better on my machine? Should I send away for a CD?

Knock of the Blue and a couple of packs of cigs for a day and you can get the memory you need from eBay.
Go to crucial.com and check out just WHAT you need.  Don't have to buy from them, but it will give you the numbers you need to go shopping.

As to Firefox .. I use the Ubuntuzilla python script from the Source Forge site.  It loads and installs the latest from Mozilla itself rather than the altered repository version and it will do it as an UPDATE to your present browser.

---

