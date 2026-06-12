---
title: "Wireless N speed limited to 65mbps"
date: 2015-08-10
forum: Networking &amp; Wireless
---

### Post by agronick on 2015-08-10
I have an Intel Advanced-N 6235 chip. [Intel's webpage for the chip ]("http://www.intel.com/content/www/us/en/wireless-products/centrino-advanced-n-6235.html")says it can go 300mbps. My router's configuration page says it goes up to 130 mbps - exactly double the speed of what I'm getting. Meaning my wireless chip is running at half speed.

So how can I get my network card to run at full speed? Anyone know where I can find info on low level wireless settings?

---

### Post by weatherman2 on 2015-08-10
300Mbps is the MAXIMUM connection rate.  In reality, you usually get much lower rates than that, for a variety of reasons.  And the connection rate changes often, maybe every few seconds, depending on what's going on.  If you are a 100 feet away from the router, your connection rate will be much less than if you are a few feet away.

How is your router configured?  Is it configured to use 40MHZ dual channels?  If not - if you are using only 20MHZ / single channel - your maximum rate will be 150Mbps.

I have a 6235 card in my Ubuntu netbook.  It does connect at 300Mbps if I am close to the router, but usually I am downstairs and the router is upstairs...and my connection rate is routinely between 81Mbps and 162Mbps (also depends what other radios are in the area, etc.)

---

### Post by agronick on 2015-08-10
I'm talking about speed right next to the router. I did some research and the reason I'm having this problem has to do with channel bonding:

> You also should use **802.11n's channel bonding** to  increase throughput. On your APs, you'll find this option labeled  'double-wide' channels. This in an ancient technique that's used to  increase throughput by using two channels at once to deliver data. Then,  as now, it works well. [http://www.zdnet.com/article/four-ways-to-get-the-most-from-your-802-11n-wi-fi/](http://www.zdnet.com/article/four-ways-to-get-the-most-from-your-802-11n-wi-fi/)

It is enabled on the router. I have no idea how to enable this in Linux. This is how you do it in windows apparently: [http://www.intel.com/support/wireless/sb/CS-025343.htm](http://www.intel.com/support/wireless/sb/CS-025343.htm)

---

### Post by papibe on 2015-08-10
Hi agronick. Welcome to the forum ):P

Are you running Trusty?

If so, try the steps explained in posts #11 and 12 [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630").

Let us know how that affect your speed.

Come here often and have fun.
Regards.

---

### Post by weatherman2 on 2015-08-10
"Channel bonding" is the same thing as the "dual channels" (40MHZ) that I mentioned above.

I did not have to enable it on my 6235 - I get it automatically, at least with Ubuntu 12.04.  I didn't have to do any tweaks to get 300Mbps.

I do get better connection with 5GHZ than 2.4GHZ, though.  There tends to be a lot of 2.4GHZ interference with other routers, wireless mice, bluetooth devices, etc. that can reduce radio performance.  I live in an area with a lot of 2.4GHZ wifi routers.  "Channel bonding" requires two adjacent 20MHZ channels, and in the US there are only 11 2.4GHZ channels (14 channels in other countries).  So sometimes finding two adjacent channels without interference is hard.  5GHZ is pretty wide open (usually more available channels) so gets better radio connections in my experience.

Keep in mind that not all wireless routers are created equal, either.  If your router manufacturer offers an update to your router's firmware, consider installing it.

---

### Post by agronick on 2015-08-10
I set it to 0. Then I went into my router and set the channel to 1. I'm now getting 117mbps. Looks like the problem is solved. It didn't use dual channels when it was set to 6 oddly. Probably was a router issue all along.

---

