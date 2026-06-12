---
title: "I want a solid list"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by joshier on 2007-08-19
I've discovered the flaky list that is [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53) and quite frankly, I'm shocked.

The Works "out of the box", is insane... most of the users mislead other people into thinking it works out of box when it doesn't, but there's many of them.

Here's one classic example 'works out of box?' "Detected and loaded OK. I have not tested actual connection."

Right, well, how is that proved and tested?.. it's not.

The list also doesn't help with the latest ubuntu. What point is there to a user stating that it works with ubuntu dapper, when people are using edgy, or feisty??.. Not useful at all. totally useless.

One of the main things which will help linux adoption, is the ability to direct people to proper hardware that is proven to work...  otherwise a bunch of people will end up splashing money out on a piece of hardware from some flaky list that some kids put 'yes works out of box' even though he really has no idea if it does or not. - thus losing all the hopes in the person(s) view of linux, and destroying any chances of that person trying to use linux.

We need a rock-solid hardware compatible list. No rubbish, No 'yes it works out of box, but you have to download the latest kernel, compile, then install dapper, and download the latest source for drivers of USB card, then compile that onto the new kernel and go into terminal to type 'sdfionas;f' enter, then setup port settings manually on ip table, then ...' and so on

out-of-box, means, it works, out of the box... Not, out of the box - and a bit of compiling, a bit of configuring, a bit of messing around...

No. Out of box means you plug it in, and it recognizes the hardware, and it finds the connection that you set it to - and it just ... works! - Nothing else to do!


I hope the community can get together again and really work on this shocking list to finally put it straight.



Right now, I've got given £50 from my friend to buy him a wireless usb/pci wi-fi device which works *actually* out-of-box, so he alone can put it in and have it working straight away.

Currently I am having to put it on hold because of this terrible list, and because of that - he is left with a computer without the internet.

Come on people, we need a decent list for our fellow geeks to help out non-fellow geeks put linux in a good light.

---

### Post by kidders on 2007-08-20
Hi there,

This is a networking support forum. If you have a specific problem someone can help you with, please do post it. With regard to the list you mentioned, note the words "Under construction". If you would like to amend it, feel free to do so.

---

### Post by SactoBob on 2007-08-21
Expressing shock and anger at the Linux community for the refusal of manufacturers to release proprietary details of their wireless cards is not appropriate.  As long as manufacturers refuse to cooperate with Linux, there are going to be problems with wireless card support.  My own shock is that so many generous folks put in so much time to reverse engineer so many products and provide solutions for Linux users.

You can bypass these wireless problems with a bridge for about $60 if you want to.

See [http://ubuntuforums.org/showthread.php?t=387871](http://ubuntuforums.org/showthread.php?t=387871)

"Help me find a fully supported pci wireless card"

Bob

---

### Post by ddrichardson on 2007-08-24
I spend a lot of time with the documentation team and often update wiki pages when I've free time - could you tell us what exactly is wrong with the current layout and what you want to see.

Bear in mind however that unless someone wishes to donate me a bunch of wireless cards we're pretty restricted to those people who have those harware/os configurations taking the time to post there experience.

As for suggesting a card - the  Intel PRO/Wireless 2200 is well supported and appears to be the card of choice with system builders providing Ubuntu laptops.

---

### Post by Darkhack on 2007-08-24
I 100% agree.  I've updated the wiki myself a few months ago for my device and I made very clear that it does work, but requires few minor tweaks.  It technically does work out of the box because Feisty does detect the device and the drivers are already installed but I edited the wiki to show that it doesn't simply because NetworkManager doesn't work properly with it and that manually configuration with the command line is required.  In my opinion, it shouldn't read "out of the box" unless it works with NetworkManager too.

I am some what busy with my college studies, but I am considering submitting some patches to NetworkManager or forking it if they are not accepted.  Work has been rather slow on it.

---

