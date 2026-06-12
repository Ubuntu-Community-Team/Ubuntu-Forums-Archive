---
title: "Media streaming over internet using UBUNTU server"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by jesternsb on 2010-09-20
Hi all, new to the forum and relativly tech savy across the board.  Need some help or direction with a project i have under taken that has hit a road block.
 
Here is the breakdown of what i would like to be able to accomplish.
 
The goal here is to setup some type of streaming media server that can be accessed externaly via the internet/ web browser.  
 
Let me give you some rational behind the end goal so you can see where i am coming from and trying to accomplish here.  
 
I have a younger brother and sister, both in college, one in Mass and one in CA.  I would like to be able to setup sometype of acess for them to be able to access the media on my network.  Currently have about 3TB of movies, TV , music....etc and want to give them access to it along with access for me to be able to access those items via external pc or smart phone.  I have recently been doing a lot of reading on home servers and thought i had found the resolutuion but have hit a wall.  
 
I have installed virtualbox and the newest version of UBUNTU server with LAMP.  I have been able to install UBUNTU server and it works and i can see apachce2 is host correctly, or seems to be when accessing via  the ip when running "ifconfig".
 
I have been unable to find any details on how to do what i am hoping and figured i would give the forum a shot.  I have to think other folks have tried to do the same with better luck.
 
The other thought/idea was if i could host a webpage that had the files acessable for download, potentially as a work around, instead of streaming them directly from the host.....really not even sure if what i am trying to do is realistic.
 
This has been a huge under taking as i have always wanted a media server but the value, for me, comes from being able to access it from outside my homer network. (currently have a nice new PC hooked directly up to the plasma so no real need for home media serving, but have experince with that and have used it succesfully on the home network).
 
Honestly i am not sure now i have went down the right path here and am hoping someone with more of a technical backround can point me in a direction here.
 
Hope this makes sense as i tried not to rant.
 
Thanks all for your help, let me know if i need to clarify any of the above.
 
Thanks again  
 
JesterNSB

---

### Post by okplayer02 on 2010-09-24
Do you have a dynamic or static ip address from your ISP. if you have a dynamic then you should use the Dyndns option. 

If you decide the second option you can use Dyndns as a way to have a domain name for ur ip address. Its a free service btw. So that is doable


With using the virtual box option you have to make sure to use networking in VB so that your Host machine is a NAT for your guest (Ubuntu) machine. You will need the Dyndns option with this also i would suggest anytime i run a server from home.

---

