---
title: "Can I install usb Modem driver in Live mode"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by terryb_au on 2011-01-07
Hi all,

 I now want to install a usb broadband modem driver in LIVE only session if possible. When in live I can't connect to internet because I have to enable a restricted driver that apparently suits the Huawei E1803, of course  Ubuntu tries to get it from the on line archive, which it can't because no connection. I went back to windows and downloaded the said driver sl-modem-daemon_2.9.11~20100718-2_i386.deb. and it's on a usb flash drive now, which I know I can see in Ubuntu.

 So, ???, what do I do when I boot back into Ubuntu (live/memory)to install the driver, preferably using a GUI, pretty clear instructions will be needed please especially if I have to use terminal interface.:confused:
I know that it will only be in memory and I would have to install it again on any new launch from dvd.
Hope you understand what I'm on about.
I searched for solution but couldn't find anything like my circumstance.

Thanks and Cheers,
Terry.

---

### Post by terryb_au on 2011-01-07
Hi again all,
Well I solved it myself and am now posting this post via Ubuntu:razz::razz::razz:
I was able to install the driver by using Synaptic, somehow I got the file to show up and was able to install it.
Well now I know it's possible, and I'm on the internet through LIVE dvd Ubuntu.
Now to have another look to see if I can remember what I did and write it down.

Cheers
Terry):P

---

### Post by terryb_au on 2011-01-08
Hi there,
Me here again,
I thought I'd update my experience of installing driver for my usb modem mentioned in my 2 posts previously. Just doing this in case some other beginner finds this post because he/she is in similar predicament.

If you are in my original predicament (no matter what usb broadband modem) you will have seen, when trying to connect, or hitting the Install driver icon, which may appear next to the connection icon in the top right menu area a pop up message to say something like this

" Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/s/sl-modem-daemon_2.9.11~20100718-2_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/restricted/s/sl-modem-daemon_2.9.11%7E20100718-2_i386.deb")  could not resolve 'archive.ubuntu.com'  "

I shut down, rebooted to windows then went to [http://archive.ubuntu.com/ubuntu/pool/restricted/s](http://archive.ubuntu.com/ubuntu/pool/restricted/s) and navigated until I found the file,  sl-modem-daemon_2.9.11~20100718-2_i386.deb  of course this was the one to suit my modem. I downloaded and saved it, in my case on a usb flash drive, usb memory stick whatever.

Now booting back into LIVE ubuntu I now open the usb flash drive, highlight the .deb file, right click on it and selected "Open With Ubuntu Software Center"  all goes very easy from there, when that program opens just hit the install button. Go into connection and set up your provider, mine was on the list. I was able to connect leaving all the defaults that the connection centre set up.  This is an easier way IMO to install the driver than the first way I achieved it(post #2), I actually couldn't work out again how I did it in the Synaptic Package Manager, some how I must have just blundered my way through.

So that's how I now do it. A driver, in my case a restricted driver, can be installed into a LIVE session, booted from DVD.

Ubuntu 10.10.

Good luck and Cheers,
Terry.:grin:

---

