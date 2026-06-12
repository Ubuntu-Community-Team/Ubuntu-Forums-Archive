---
title: "New posters: broken connection? Help us with some information."
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by nixscripter on 2008-02-24
(Hopefully, this will be made a sticky.)

This post is a suggestion to everyone who posts a "my connection doesn't work" thread. I have answered a lot of these, and would suggest a list of things to include in their first post, and a short overview of why.

When someone has a problem connecting to a network, there are generally a few areas where the problem is:

1. The physical devices involved, such as network cards and ethernet cables.
2. The link between those physical devices, such as a weak wireless connection.
3. The computer's understanding of the data paths, such as routing tables and IP addresses.

Therefore, I would request that new posters provide some information, and run some commands which gather information relating to these three areas.

First, I have encountered several people who, either through understandable ignorance or simply speed of typing, fail to give useful information in their problem description. Often, I have to ask them questions to determine a path to a diagnosis. Here are some suggestions of things to include in the first post in order to save this process.

1. **What you have tried, being specific as possible.** "I can't get to google.com" is a lot more specific than "the internet/web doesn't work." In fact, what your browser said when you tried google.com helps a lot; there is a big difference between "unable to connect" and "connection refused, try again later."

2. **Some basic information about the state of the hardware.** If the ethernet card has a light on it, for example, what does it do? This might rule out simple things like "oh, the card isn't seated." For wireless cards, some have an external switch, as well as status lights. Makes and models of cards are useful and should be mentioned as well.

3. **Information about the software.** There are several indicators of network activity built into the GUI, for example the networking applet. When trying things, what does it do, and what states does it go through?

Second, I ask for these commands to be run. They are for printing diagnostic information. Please post the results in [CODE] blocks so that formatting will not be interpreted by the forum's scripting. These commands are to be run in a terminal window in some order.

**ifconfig -a** will list the network interfaces on your system. These are the devices that packets can be sent down. It will show connection information about each device, such as IP address, and allow for detecting problems in the 3rd area.

**route -n** will list the mapping between IP addresses and physical devices when it is deciding where to send the packets. This is used to detect problems in the 3rd area.

**iwconfig** will list information about wireless cards if that is part of the problem, such as the network connected (if any), and signal strength. It helps in the 2nd and 3rd areas.

**lspci** lists all of the devices on the PCI bus. Generally, this includes all of the ethernet and wireless cards. It helps detect problems in the 1st area by verifying the kernel knows your card is plugged in.

If everyone who started a new thread did this, I would certainly appreciate it, as it would make my diagnoses faster.

Good luck to everyone with a problem.

---

