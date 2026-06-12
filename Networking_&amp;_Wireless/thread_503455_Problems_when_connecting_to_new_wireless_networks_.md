---
title: "Problems when connecting to new wireless networks and back"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by Ginigrace on 2007-07-17
At home I have an unsecured wireless network that was working great with my computer running Feisty Fawn. This past weekend I traveled with the computer and signed on to an unsecured wireless network in a hotel room. Everything worked great in the hotel. I came home and while I can "see" my home wireless network the computer is not able to connect automatically unless I select "Connect to other wireless network" then it will connect to my home wireless network, but the computer does not remember and I have to go through this each time turn the computer off or hibernate. Right now when I "hover" the mouse over the network symbol I get the message "Wireless network connection to 'GinsNetwork' (95%) which is typical. I have "Enable Networking" and "Enable Wireless" both checked. I'm using the ndiswrapper driver if that makes any difference.

When I go to "System" --> "Administration" -->"Networking" -->Password and see the "Network Settings" the first item "Wireless Connection, Roaming mode enabled" is not checked, but when I right click and bring up "Properties" on it I see the tick box for "Enable Roaming Mode" is checked! 

Can anyone give me a clue what's happening and how to fix the problem?

---

### Post by fdrake on 2007-07-17
> **Ginigrace said:**
> At home I have an unsecured wireless network that was working great with my computer running Feisty Fawn. This past weekend I traveled with the computer and signed on to an unsecured wireless network in a hotel room. Everything worked great in the hotel. I came home and while I can "see" my home wireless network the computer is not able to connect automatically unless I select "Connect to other wireless network" then it will connect to my home wireless network, but the computer does not remember and I have to go through this each time turn the computer off or hibernate. Right now when I "hover" the mouse over the network symbol I get the message "Wireless network connection to 'GinsNetwork' (95%) which is typical. I have "Enable Networking" and "Enable Wireless" both checked. I'm using the ndiswrapper driver if that makes any difference.

When I go to "System" --> "Administration" -->"Networking" -->Password and see the "Network Settings" the first item "Wireless Connection, Roaming mode enabled" is not checked, but when I right click and bring up "Properties" on it I see the tick box for "Enable Roaming Mode" is checked! 

Can anyone give me a clue what's happening and how to fix the problem?

there is an option in which you can save your profile network settings (ex. work-wifi , home-wifi) so each time you travel you just select the place (or profile) and it works right the way.
i have no idea why your Roaming option stays checked.

---

### Post by Ginigrace on 2007-07-22
I just went to System, Administration, Network ...... turned off the wired option,  turned on the wireless roaming option and am now connect wirelessly. I've also tried to save the "current network configuration as a location,"  this what you were suggesting? I had tried to save this before, but with the wired option selected and maybe that was the problem.

---

