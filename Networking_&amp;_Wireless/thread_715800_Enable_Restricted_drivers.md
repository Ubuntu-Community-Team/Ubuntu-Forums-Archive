---
title: "Enable: Restricted drivers"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by Paris Heng on 2008-03-05
Dear,

For madiwifi driver installation, how to [COLOR="Red"]**enable the restricted drivers**[/COLOR]? Once I install the madwifi-0.9.4, I even cannot boot my ubutnu.

***For other editions just enable restricted drivers***

Reference; [https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint#head-1bfcd0ee3455ef3e70ea76c5356edc010ecae741](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint#head-1bfcd0ee3455ef3e70ea76c5356edc010ecae741)

Please help.

---

### Post by {BzF}~JOKesTER on 2008-03-05
If You Cannot Boot Your Computer I Suggest Removing The Wireless Card From Your Computer When It Is Off - And Then Try And Boot.

I'd Like It If You Were More Specific On The Problem Your Having Please.
Normally To Enable Restricted Drivers Browse To:

Tray >> System >> Preferences >> Control Center >> Restricted Drivers Managment.

If I'm Not Addressing Your Actual Problem Please Post A Reply In This Thread.

---

### Post by Paris Heng on 2008-03-05
Thankx,

I now using **Ubuntu 7.04**. Previously I using **Madwifi-0.9.3.1**. And the card work fine, now I am using the **Madwifi-0.9.4**. The Wifi card is **DWL-G520** (Atheros), is a PCI type. 

I only can boot my PC in Madwifi-0.9.3.1. When I remove the old madwifi, install with new Madwifi (in this case, Madwifi-0.9.4). When I re-boot, just the PC can't re-boot, it hang half way during loading. The PC only can boot when it using Madwifi-0.9.3.1 and when the PCI wifi card is removed. What happen to the new madwifi?

---

### Post by {BzF}~JOKesTER on 2008-03-05
It's Possible That The New Madwifi Doesn't Support Your Card.

The Older Madwifi May Have Drivers That Are Compatible But The New Version Doesn't.

If You Have Any Other Questions Please Feel Free To Ask.

Hope This Helps!!

---

### Post by {BzF}~JOKesTER on 2008-03-05
Have You Considered Using ndiswrappper For Your Drivers?

Heres How: - {You Will Need The Attached Driver - Or Use Your Own Of A Disc}
{Make Sure If You Do Use Your Own That The Folder Contains Both The .inf And The .sys Files}

[ATTACH]61663[/ATTACH]


1. Goto The Synaptic Package Manager And Put In:

ndiswrapper

Install:

ndiswrapper-common

2. Extract the Drivers Attached To The Directory Of Your Choice.

3. cd To The Folder DWL-G520

4.Type: ndiswrapper -i net5211.inf

It Should Say "Installing..."

5.Type: ndiswrapper -m

6.Type: ndiswrapper -mi

7.Type: ndiswrapper -ma

8.Type: lsusb       #Assuming This Is A USB Card.

9.Find Your Card Listed And Copy The XXXX:XXXX Numbers -{With The Colon}

10.Type: ndiswrapper -a XXXX:XXXX net5211

{Note: Replace The XXXX:XXXX With Your Code You Copied - Example: 0468:0a60}

Restart And Thats It!!!

Hope This Helps!:KS

---

### Post by Paris Heng on 2008-03-05
thanx

---

### Post by {BzF}~JOKesTER on 2008-03-05
No Problem,

You Need Anything Else Just Let Me Know

:popcorn::KS

---

