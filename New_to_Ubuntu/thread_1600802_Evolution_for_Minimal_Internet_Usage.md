---
title: "Evolution for Minimal Internet Usage"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by Nanix on 2010-10-19
I am moving to a rural area where satellite is the only option. To conserve bandwidth I plan to switch to an offline mail and RSS reader (previously I used Gmail and Google reader), in this case Evolution. I am open to suggestions if you have a client that might serve my purposes better.

I have set Evolution up using IMAP and it seems that evolution wants to constantly be connected to the internet for downloading individual messages and changes. I want Evo to download/upload only when I click send receive. I also want it to download everything at once.

I have yet to install the RSS plugin but I hope that it will work in a similar way.

How can I make evolution do this? I have tinkered with the settings but it doesn't seem to do what I want. Any suggestions on another approach are welcome.

---

### Post by Old_Man_Unix on 2010-10-19
> **Nanix said:**
> 

I have set Evolution up using IMAP and it seems that evolution wants to constantly be connected to the internet for downloading individual messages and changes. I want Evo to download/upload only when I click send receive. I also want it to download everything at once.



This is simply the way the IMAP protocol works.  It assumes a continuous connection to the server.  

By default, Evolution is set up to follow the protocol.  But it is a very flexible mail client and you can change that behavior if you want to.

What you want to do is to implement what is sometimes called "offline IMAP" or "disconnected IMAP".   You can do this right inside Evolution - you don't need any plug-ins or additional applications.

In Evolution go to Edit->Preferences. Select the IMAP account and go to Edit->Receiving Options.  Check  "Automatically synchronize remote mail locally".  Warning - this will apply to the whole account - **all** the folders -and will launch as soon as you connect to the server. 

If you just want to choose individual messages for storage locally, you can do that as well  but you cannot use the IMAP synching features.   Create a local folder or folders.  Establish your IMAP connection, go to whatever folder you want to, select the appropriate messages, and copy them to the local folder.  

You must stay connected during these operations.  If your connection is so unreliable that you can't be sure of this, you might want to consider switching to a POP protocol which is generally better for unreliable intermittent connections.    That has its limitations as well so this is a decision you will have to make. 

As I said,  Evolution is a very flexible mail client and I don't think you are going to find a better one for these purposes.

---

### Post by Rex Bouwense on 2010-10-19
I have been using Thunderbird with Ubuntu for a couple of years (POP protocol) and have been completely satisfied.  Since we are on the road for all 12 months of the year, I would consider that a good thing.

---

