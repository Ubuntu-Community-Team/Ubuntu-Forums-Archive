---
title: "IPV6 timeouts, Kubuntu 14.04"
date: 2017-09-04
forum: Networking &amp; Wireless
---

### Post by mmmmna on 2017-09-04
Over at this thread, [https://ubuntuforums.org/showthread.php?t=2369568](https://ubuntuforums.org/showthread.php?t=2369568) I had been having issues with using certain repositories. Certain servers are failing to deliver, it looks like if I force Synaptic to use IPV4 connections (from a command line), those servers which previously timed out will now work fine under a forced IPV4.

I'm presently on Comcast, which is a cable connection. My troublesome desktop system uses a wired ethernet connection leading to a wireless client adapter (TPLink TL-WR700N), connecting to the late model wireless device which Comcast sent us. With the same desktop, same version of Kubuntu, same ethernet to wireless adapter setup, this all worked fine last fall, but my wireless adapter was connected to a Verizon Fios box back then. Different ISP.

Anyways, now I'm on Comcast, I get stalls. From the previous thread, I learned that the IPV4 path works fine.

I googled IPV6 timeout. I discovered that Comcast has a readiness test suite.

When I test my service according to the Comcast test suite (served from a Comcast mirror), I get interesting results.

I went to [http://test-ipv6-ct.comcast.net/](http://test-ipv6-ct.comcast.net/):
```
&#65532;Your IPv4 address on the public Internet appears to be xx.xxx.xxx.xxx
Your Internet Service Provider (ISP) appears to be COMCAST-7922 - Comcast Cable Communications, LLC, US
No IPv6 address detected [more info]
When a publisher offers both IPv4 and IPv6, your browser appears to be happy to take the IPv4 site without delay.
Connections to IPv6-only sites are timing out. Any web site that is IPv6 only, will appear to be down to you.
To ensure the best Internet performance and connectivity, ask your ISP about native IPv6. [more info]
Your DNS server (possibly run by your ISP) appears to have IPv6 Internet access.
Your readiness score
0/10	for your IPv6 stability and readiness, when publishers are forced to go IPv6 only
```

And the test results were:```
How this test works: Your browser will be instructed to reach a series of URLs. The combination of successes and failures tells a story about how ready you are for when publishers start offering their web sites on IPv6.

Click to see Tests Run

Test with IPv4 DNS record
ok (0.628s) using ipv4
http://ipv4.test-ipv6-ct.comcast.net/ip/?callback=?
Fetches an object that has just an A record in DNS. This is expected to use IPv4. IPv6-only users might still reach this, if their provider has employed a NAT64/DNS64 or proxy solution.
Test with IPv6 DNS record
timeout (15.009s)
http://ipv6.test-ipv6-ct.comcast.net/ip/?callback=?
Fetches an object that has just an AAAA record in DNS. This is expected to use IPv6. Users not yet on the IPv6 Internet are likely to see this fail. As long as it fails quickly, it will be OK - for now.
Test with Dual Stack DNS record
ok (0.704s) using ipv4
http://ds.test-ipv6-ct.comcast.net/ip/?callback=?
This is the most important test. This verifies your browser can connect to a site that has both IPv4 and IPv6 records published. IPv4 only hosts should connect fine (using IPv4).
If this test fails or times out, you can expect major problems as publishers start offering their sites on IPv6.

Test for Dual Stack DNS and large packet
ok (0.604s) using ipv4
http://ds.test-ipv6-ct.comcast.net/ip/?callback=?&size=1600&fill=xxx...xxx
Validates that you can connect to a dual-stack server (like the ds test); and that you can send/receive large packets on that connection. If this test times out for any reason, it indicates trouble for World IPv6 Day.
Test IPv4 without DNS
ok (0.697s) using ipv4
http://96.119.0.221/ip/?callback=?
This will try connecting with a literal IPv4 numeric address. This should work for most people, unless they are running IPv6-only. If the first test worked, but this fails, it likely confirms your provider is using NAT64/DNS64; you'll need to only try connecting using hostnames instead of numeric IP addresses.
Test IPv6 without DNS
timeout (15.010s)
http://[2001:558:fc00:100:f816:3eff:fe2b:6488]:80/ip/?callback=?
This will try connecting with a literal IPv6 hexadecimal address. The primary purpose of this test is to separate out your connectivity on IPv6 from your ability to fetch DNS for it. A secondary purpose is to see if you have Teredo enabled; some systems may only use Teredo when an IPv6 address is in the URL.
Test IPv6 large packet
timeout (15.012s)
http://mtu1280.test-ipv6-ct.comcast.net/ip/?callback=?&size=1600&fill=xxx...xxx
Validates that IPv6 requests with large packets work. If this test times out, but other IPv6 tests work, it suggests that there may be PMTUD issues; possibly involving IP tunnels. Double check to make sure that ICMPv6 Type 2 ("Packet Too Big") messages are not filtered by your firewall.
Test if your ISP's DNS server uses IPv6
ok (0.623s) using ipv4
http://ds.v6ns.test-ipv6-ct.comcast.net/ip/?callback=?
(This is bonus credit)
This is a test of your ISP's resolver (instead of a test of your host). If this test passes, your DNS server (often run by your ISP) is capable of reaching IPV6-only DNS authoritative servers on the Internet. This is not critical (at this time) for you to reach sites via IPv6.
Find IPv4 Service Provider
ok (0.644s) using ipv4 ASN 7922
http://ipv4.test-ipv6-ct.comcast.net/ip/?callback=?&asn=1
Attempts to identify what Internet Service Provider you use for IPv4. This may be different from the marketing name you see in your local market; or may reflect a previous company name. The name shown reflects how it is known in the network operator community.
Find IPv6 Service Provider
timeout (15.006s)
http://ipv6.test-ipv6-ct.comcast.net/ip/?callback=?&asn=1
Attempts to identify what Internet Service Provider you use for IPv6. When the IPv4 name and the IPv6 name don't match, it may suggest that you're using a tunnel; or some form of third party provider for IPv6.
If the summary results indicated problems, you (or your technical support) may be able to use the information above to diagnose the issues. Each of the test urls and their results is shown on the left side. To the right you'll see a description of what that URL was designed to test.

After each test is ran. The summary page attempts to look at the results If the summary doesn't seem to make sense given the symptoms recorded above, or if you need further assistance, please feel free to contact us.


```Every IPV6 test went to timeout.

Not quite sure where to make changes. Thinking I'll peruse the cable modem configuration soon, but naivety warns me to make no changes unless someone posts who is familiar with IPV6 configuration issues on very recent model Comcast hardware (issued to us in June 2017).

Occasionally, other people on the same access point see stalling issues, but I'd be guessing to say they have the same problems. It looks like my whole connection chain isn't properly supporting IPV6. 

What could be an effective solution - reconfigure the cable modem?

---

### Post by BenginM on 2017-09-04
Hiya, I would contact the ISP to conform IPv6 is natively supported & report this behavior  .  and ask them how to configure the cable with the network setup you have to be used with GNU/linux OS.

---

### Post by him610 on 2017-09-05
It also said this, if you clicked on[I] [more info]
[/I]
> You appear to have no IPv6 at this time..

You appear to have no IPv6 address.

It looks like you have only IPv4 Internet service at this time. Don't feel bad - most people are in this position right now. Most Internet service providers are not quite yet ready to provide IPv6 Internet to residential customers.

Many of the visitors to the site are new to what IPv6 is. If you don't know why IPv6 matters, see the Why IPv6 FAQ. This will give you a bit of background of what to expect with IPv4 in the coming months and years; and perhaps some incentive to ask your ISP when they will offer IPv6.

If you strongly believe you have IPv6, but we were unable to detect it: it means one of a couple of things. Either your organization is blocking the use of IPv6 to talk to the outside Internet through network policy; or perhaps what you see with IPv6 on your host is not a global address. Any address starting with "::", "fc", "fd", or "fe" are unable to work with the public IPv6 Internet.

If you are savvy with technology, you can be an early adopter of IPv6, consider learning more about 6to4 providers (managed 6to4 tunnel services). The use of automatic tunnels is discouraged [see more].



---

### Post by mmmmna on 2017-09-06
Thank you to both of you!



"You appear to have no IPv6 address."

The weird part for me is that the IPV6 test is served from **Comcast**, the test is testing **Comcast** IPV6 internet access.
Why are they admitting they aren't supporting IPV6?
No need to answer that, but it helps you to understand what I'm up against.

---

### Post by mmmmna on 2017-09-10
> **BenginM said:**
> Hiya, I would contact the ISP to conform IPv6 is natively supported & report this behavior  .  and ask them how to configure the cable with the network setup you have to be used with GNU/linux OS.
I just did contact Comcast, and the result of the testing we performed shows that only this ONE system out of several tested devices is failing IPv6 testing. A Chromebook totally passes, my Nextbook Ares 8 tablet totally passes, my Android 6 Tracfone passes the test, all are on the same home network.

The problem is my desktop systems network configuration.

I have a bit of work to do, to see if I can get an old Broadcom wifi card to function inside the box, just in case the problem exists in the client adapter I'm using.

---

### Post by mmmmna on 2017-09-12
I installed the Broadcom wifi card, but I couldn't get it configured. It's one of those firmware/STA things. Junk.

This next step became the final test.

I swapped out the TPLink TL-WR700N which was connected to this desktop system and had worked fine until a couple months ago when I switched ISPs and also returned to Kubuntu, and instead of the TL-WR700N, I inserted a Netgear WNCE3001. Both are client adapters connecting to my ethernet port, which adapters allow my desktop PC ethernet port to connect to my wireless network. Yes, the TPLink **TL-WR700N** was the problem. I was unable to locate any setting inside the WR700N which mentioned IPv4 nor IPv6. There simply is not any setting stating anything about address schema.

I am having no IPv6 problems with the WNCE3001, my desktop system now passes the IPv6 tests, and all I did was swap client adapters. My ethernet port was configured the same way for both client adapters.

I'm guessing that the TL-WR700N is mishandling IPv6, but beyond that, no clues.

Thanks for thinking about my issues.

---

