---
title: "Creating a wifi repeater using 2x ubuntu machines."
date: 2015-10-17
forum: Networking &amp; Wireless
---

### Post by Jammyjamjamman on 2015-10-17
(N.B.: I understand that this is a sub-optimal solution to repeating the wifi, but for now this is my only option. Also I did all of this using the respective network gui's for each device.)

I've been trying to make a wifi repeater using a dell inspiron 910 running lubuntu15.04 (32bit), and a hp-dv7-7102ea running Kubuntu15.04 (64bit). I did all of this with the firewall deactivated on both devices.

The basic plan of the repeater is:    [main_router] -(wifi)-> [dell] -(ethernet)-> [hp] -(wifi)-> [transmits wifi to all other devices]
 where anything between [] indicates a device, and -(<interface>)-> is the method which the device before the arrow connects to the device after the arrow. The router is the source of the internet for this problem.

My first test was to connect the hp to the main router, using the ethernet cable. This was so I could set up wifi-sharing. I then enabled wifi-sharing on the hp, and connected my phone to my hp's wifi connection. Voilà! my phone can connect to the hp's network connection, and connects to the internet with no problems.

Next test, was to set up the dell to share its connection through its ethernet port. The dell was connected to the router over the wifi. I set the ethernet port connection in the dell's network settings to "shared to other computers". The hp's wifi was switched off. The hp was then to the dell via their ethernet ports. Once again, the hp connects to the dell, and has no problem connecting to the internet through the dell.

The final step is where everything seems to go a bit pear-shaped.
Finally, after completing the previous step, I switched wifi-sharing in the hp back on. My phone once again has no problems connecting to the hp laptop, and the hp laptop still *appears* to be connected to the dell over the ethernet (according to the network managers). However, the hp is no longer able to connect to the internet, and also neither can any device connected to the hp. The dell is still connected to the internet during this step. As soon as I switch off the wifi-sharing on the hp, the hp regains its connection to the internet.

I tried this with the laptops swapped over (i.e. the hp is connected to the router, and the dell is sharing its internet connection using wifi). I get the exact same results.
I'm unable to work out what the problem here is. Sharing internet over wifi and sharing over the ethernet both appear to work fine. But as soon as I try to share using both chained together, it all goes wrong.

---

### Post by Jammyjamjamman on 2015-10-20
In case anyone is interested, the problem was simply over-usage of the same ip. When the network manager is used to share internet over the ethernet/wifi, it uses the address 10.42.0.1 as the address of the hosting component. This meant my hp machine was requesting data as 10.42.0.1, then the dell didn't send the data it recieved for the hp, to the hp, because it thought the data was for itself as it also had the address 10.42.0.1.

---

