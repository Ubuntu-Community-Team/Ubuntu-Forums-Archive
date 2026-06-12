---
title: "How to measure network traffic?"
date: 2015-03-27
forum: Networking &amp; Wireless
---

### Post by Icetoad on 2015-03-27
I am trying to figure out which one of the channels (1, 6 or 11) would be appropriate for my application to transmit data.
What metric would be best suited in guessing the lesser congested channel?

---

### Post by TheFu on 2015-03-27
Use a wifi analyzer (android or wicd have these) to see what others around you are using.  Some routers have a **site survey** built in. Tomato does. Also, the 5Ghz bands are much less congested, if your equipment can do that.

Basically the router sets which channel is used and the clients or applications have ZERO choice. For the router setup, pick the least used channel in the area. The channels today may not be the same as the best channel to use tomorrow. Checking every few months is smart.

---

### Post by Icetoad on 2015-03-28
Thanks for your valuable input.

What is the metric I should keep in mind when choosing the right channel?
I can already use wireshark/tcpdump to monitor the channel...should I look at pps? rssi?

For the context, I am working on ad hoc topology where the nodes automatically find the least congested channel and shift transmission over that channel for faster data transfer.

---

### Post by TheFu on 2015-03-28
Look for the lack of other systems using that channel OR any overlapping, nearby channels. Get **WiFi Analyzer** in the google Android store (free) to see what I mean. They have a channel selector and graph tool that shows which channels are being used by nearby devices on both 2.4 and 5Ghz bands.

BTW, sometimes, in crowded areas, you'll need to pick a different channel than 1, 6, 11.

---

### Post by Icetoad on 2015-03-28
Yes yes I have used the Wi-Fi Analyzer long back, I guess it gives the signal strength of nearby networks in dBm. But does high signal strength always mean high network traffic?

I am little confused with metric I need to rely on, and how to get those values from IP suite.

The system I am trying to program is a FTP server which first finds the least congested channel then asks the client to shift to that channel before connecting again and transferring the file.

---

### Post by TheFu on 2015-03-28
There are very few reasons to use plain FTP today  [https://www.google.com/search?q=stop+using+ftp](https://www.google.com/search?q=stop+using+ftp) and many reasons not to use it. For sharing files with the world, bt, http are options. For sharing with specific people, sftp is really the main choice.

Interference and low s/n is a known issue for performance, but those aren't the only things. Short of testing the throughput - nothing is 100% that I know.  Newer routers support channel sharing better with the newer protocols. Limiting yourself to 2.4Ghz is a bad idea if performance is the main goal for your tool.

---

### Post by SeijiSensei on 2015-03-28
You can see a list of the channels in use around you with with the iwlist command:
```

$ sudo iwlist wlan0 scanning  |  grep Channel:
                    Channel:8
                    Channel:6
                    Channel:6
                    Channel:6
                    Channel:1
                    Channel:1
                    Channel:11
                    Channel:11

```

---

### Post by tgalati4 on 2015-03-28
Well, I am in a very congested wifi area and I have to use channel 4 for those devices that don't have 5 GHz.  Since most cable/phone company routers routinely hop between 1, 6, and 11, you don't have much choice, but rarely is 4 used.  Yes, you get side-band interference, but some packet resets are better than slow access, so you have to find the compromise that works.

First rule:  Use wired as much as you can.
Second rule:  Use 5 GHz band for all devices that have a 5 GHz transceiver, except you get less range for large houses or properties.
Third rule:  Find better neighbors.

You could write a script to examine *netstat* and suggest a channel change based on bad packets:

> tgalati4@Mint17 ~ $ !474
netstat -s | grep received
    148143 total packets received
    28 ICMP messages received
    109 connection resets received
    131423 segments received
    248 bad segments received.
    13290 packets received
    3653 packets to unknown port received.
    14782 acknowledgments not containing data payload received
    237 DSACKs received


---

### Post by TheFu on 2015-03-28
Nice responses from SeijiSensei and tgalati4.

A small suggestion:```

sudo iwlist wlan0 scanning  | egrep 'ESSID:|Channel:|Quality=' |more
```
to add the SSID and signal strengths to the output.

---

### Post by Icetoad on 2015-03-29
First of all, thanks SeijiSensei and TheFu, I am using the enhanced command TheFu has mentioned.

TheFu, what do you suggest I should do to increase the scalability of the system over more channels?

I only have experience working with 802.11b standard, is there much high level difference if I shift to a more recent version of WiFi? 
As tgalati4 has pointed out 5GHz has lesser range, and it is illegal to use in open in Japan and the system I am programming is for a real world mobile node scenario.

---

### Post by Icetoad on 2015-03-29
I am facing a new issue here, my network interface is not switching channel, it says it is busy even when I "down" it before switching.

---

### Post by Icetoad on 2015-03-29
> **tgalati4 said:**
> Well, I am in a very congested wifi area and I have to use channel 4 for those devices that don't have 5 GHz.  Since most cable/phone company routers routinely hop between 1, 6, and 11, you don't have much choice, but rarely is 4 used.  Yes, you get side-band interference, but some packet resets are better than slow access, so you have to find the compromise that works.

First rule:  Use wired as much as you can.
Second rule:  Use 5 GHz band for all devices that have a 5 GHz transceiver, except you get less range for large houses or properties.
Third rule:  Find better neighbors.

You could write a script to examine *netstat* and suggest a channel change based on bad packets:

Yes I was thinking along the same lines, as the number of packets received would give a better picture of channel traffic. I will try this one out and let you know the results :)

Just thinking if the signal strength will vary wiith multiple connections over a single channel, I think the plain monitoring of signal strength on any channel would only give signal strength of the strongest link in the surroundings, defeating the purpose.

---

### Post by tgalati4 on 2015-05-02
This is a difficult Use Case.  Since you can't use 5 GHz, you are limited to 2.4 GHz.  Packets can fail for a number of reasons.  Even though you are transmitting digital signals, ultimately, analog signals are generated and received.  So when square waves get rounded or when constructive interference results in doubling of signal strength for short periods of time, you will have communication problems.  I'm only suggesting to stick with the packet layer as that is the real measure of performance.

If you read technical papers on how to set up distributed wireless-G at a conference, reducing signal strength often helps with connectivity by reducing collisions and retransmissions.  Without knowing more about what you are trying to accomplish, giving specific advice is difficult.

As far as the meaning of netstat messages:  [http://networkadminkb.com/KB/a265/netstat-statistics-and-their-meaning.aspx](http://networkadminkb.com/KB/a265/netstat-statistics-and-their-meaning.aspx)

You could write a rule when bad packets exceed 1% hop to a different channel.  Try ignoring signal strength and see how your system performs.

Most channel-hopping algorithms in routers seem to be simple and not very effective in my experience.  I often have to use counter-intuitive methods to get better throughput.

---

