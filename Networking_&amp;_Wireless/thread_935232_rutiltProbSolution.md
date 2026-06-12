---
title: "rutiltProbSolution"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by Rodney2 on 2008-10-01
I am submitting this in hopes of alleviating some of the frustration I had in getting rutilt to work with my Zonet USB wireless card.  No problem with the card, only my lack of knowledge on how to use rutilt.  So, from the start, here is what I have to do to get my wireless access working:
Open terminal by going to Applications/Accessories/terminal
type in rutilt
	When I do this the window for rutilt opens with the six folders listed across the top 
		Link Status/Statistics/Profiles/Site Survey/Options/RT73WYLAN
Click on the Options flag;
	you will see a box in the upper right quadrant with either the word “up” or “down” in it.  If it is not saying “up” click on it and it will change to “up”.
You will probably be asked for your pass word at this time, if so type it in.
Now click on “Site Survey” and click on scan.  If your router or wireless signal is present, you should see your SSID (your site name) listed along with any other active wireless signals present in your area.
Highlite your SSID and a new window should show up called “New Profile”
fill in the necessary data by giving the profile a name, enter your SSID (the name of your router which you assigned when you set up your router) and channel number.  I left the Mode as it appeared-don't know if I was lucky and it was right or ???, input my channel ( I had set that when I set up the router and it should have shown up in the scan of your SSID.  I left the Authorization as WPQPSK and the error ip as TKIP (I do not know what this means yet but that is what worked for me).  Of course I had to type in the key that I assigned as the password for my router when I set that up.  I then hit OK and the New Profile window dissappeared.  I then highlighted the SSID in the Site Survey window and hit “Connect”.   Ureka, I was now connected.
	I do not know how many hours I spent finding out what worked here and am not sure that it will work for you but, if it does, it may save you the time I wasted.  Rodney  PS, if any of you have a more streamlined way or find errors in this, please advise.   Thanks

---

