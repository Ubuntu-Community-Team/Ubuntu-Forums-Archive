---
title: "Blueman tethering"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by HarrisonNapper on 2009-11-18
IMPORTANT NOTE: Please disregard the below information; the problem was between the keyboard and the chair. For you wandering googlers out there, the other package is libmbca0 and the first reason I was getting a connection failed error was because the bluetooth on my phone was off (I know, I know, pretty blatant thing to overlook). However, I still got the error when I turned it on. This seemed to be resolved by going to Setup and setting up a new dialup network connection.

I had never really tooled around with my phone using bluetooth up until today. After helping someone on the forums look at a bluetooth issue, I thought it might be fun to tether my phone.

So I used this guide: [http://ubuntuforums.org/showthread.php?t=1317203](http://ubuntuforums.org/showthread.php?t=1317203) to tether my phone via USB.

The problems started happening when I was presented with three options: AT&T, AT&T Tethering, and AT&T Tethering (with data acceleration). I looked around for the meaning of those and I found a little bit of information, but I figured I could do the third option out of curiosity and then just go back and change the option later if I wanted to. I was wrong.

So the connection didn't work and, unable to find another solution, I simply removed the connection from network-manager. Then I went in to set up another dial up service and I get the error "Connection Failed: Does Not Match". I googled this error. I literally got nothing.

So at this point I figure that I've done a pretty good job of botching the whole thing, so I sudo apt-get remove --purge blueman and sudo apt-get install blueman. Two problems now: the remove --purge got rid of a package and X decided it was restart time at that point, so I don't remember the package. Is there a way to go back in terminal output history to find it? I'm still getting the same Connection Failed error. Has anyone ever seen this error and are there any known solutions?

Thank you in advance for your time; hope it wasn't tl;dr.

---

