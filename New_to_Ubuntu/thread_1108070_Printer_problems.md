---
title: "Printer problems"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by carnauth on 2009-03-27
Well I spent a hour or longer making a post last night... I really hate asking dumb questions, I dont have the time to give much info and am a bit miffed about the post being deleted.. 

i shared my printer and published it and set it to allow printing from inet... 
what else do i do..



sorry if you need mor info i am at work...
got to go

---

### Post by HermanAB on 2009-03-27
BTW, posts don't get deleted on purpose, the forum is overloaded and the database loses posts all by itself - it is nothing you did!

Soooo, I cannot answer your question properly since I don't know what the problem is, but maybe this will help:
[http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

---

### Post by carnauth on 2009-03-27
well i had more info in there last night but basically it is a fresh install of 8.10, I dont know what all was on it default... I tried a couple things to see if it would help.. it appears that i am unable to connect for some wierd reason 

I have printer shared and published also set for internet printing and remot administration 
i can acces the rem admin and it looks good and seems that everythings fine... when i browse to the pc via windows it says the printer status is ready... soon as i add it and try to connecct it goes nuts onme,...

i have it set to allow ussage to everyone but... and theres no ppl in the deny list.. however it still gives the error "Access denied, Unable to connect"
I tried to turn off the firewall that it said that may need to be disabled 
looked online and tried to disable the firewall(leaving work now,gotta end transmission) using "ufw disable" and also "iptables -F"

gonna have to head.. but i think its something in the conenction.... 
I thouhgt it could be samba conf but sempt that it was fine till i try to connect it prints from local but xp users cant connect. used the cups admin and did a modify printer and tryed a couple different device tryed to sety it to samba device dfor windows networks still got same error tryed 4 different combinations and get same error all the time....



dunno but i gotta head 


Many thanks in advance to anyone that gives me som good pointers..

---

### Post by Sef on 2009-03-27
>  I really hate asking dumb questions, I dont have the time to give much info and am a bit miffed about the post being deleted.. 

1) The only dumb question is the one that is unasked.   All others are smart questions.

2) There was a hic up some where in the system.   Sorry that happened to you.

---

### Post by LowSky on 2009-03-27
what kind of printer, how is it attached to the network.

I'm sory the forum somehow lost your Old post but to help w need the info again. thanks

---

### Post by listerdl on 2009-03-27
I though that printers work as a plug and play idea - that linux finds the correct driver....i must be wrong though especially since ive never tried....

---

### Post by carnauth on 2009-03-28
whoops bout forgot
HP-PSC-1210v(shows as psc1200series,driver=psc1200series foomatic/hpijs)
Well no biggy.. was just sad that I spent so long typing the stinkin' thing. Anyway I wish i could change thread title. I think the other one was titled network printer headaches, dont know y i didnt put up shared or networked... Ubuntu did fine for detection of the printer, its plugged in directly via USB.  Works fine for me from the box or the Ubuntu side of the house.   I just seem to still have probs pringting from windows boxes. Theres three xp machines that use it and two ubuntu, ubuntu does fine for printing... I even have ubuntu,horrible as it is, set up to connect to the other printer via the "Windows Printer(smb)" It connects to ubuntu and prints via samba but xp hates it...

I get two sysinfo popups in windows when adding the printer, first off reg M.$. B.S."... installing driver.... trust source..."
then the baddie!
"the server for the printer does not have correct printer driver installed......" then it wants me to install the driver. I got two laptops with the printer driver installed, & it works fine plugged in usb style.I cant choose exact model, lookin' around it seems that if exact is not applicable choice to go with"ms color publisher printer" or somthink very similar under the generic tab.. no go there .
Bright Idea
Cchanging drivers over from generic to the real ones already on my pc dont do it either... plus they got a 120MB+(no individual driver files) install sux I found the drivers in temp folder during install.. no inf so it would not load from the add printer  just use the drivers without the inf file...

Dunno I think it might be somthing with the samba.conf not sure if i need to edit it cuz I only found a few other cases similar and looked like the person figured it out by them selves. u know the post's. The ones asking adn then they never come back just gotta think they fixed it(sumptin simple) or reverted back to MS$(horrifying ordeal). I am leaning towards the first one..(hopefully.) 

From the hours i spent tweaking it different ways an trying again, I came to the conclusion that once you have it:
1. Installed(chek)
2(&3). It is set to be shared and accepting jobs(chek chek{yes its enabled})
3(or4). Set to publish shared printers(chek)

only thing that seems really off about it is it says not published,check server settings. check settings and its set to publish.. I see it from all other pcs so ?? what Is it lying to me published or not. I can print from Ubuntu->Ubuntu via SMB. I just feel like somthing stupid is off somewhere.. dosent add up right in my head..


Oh well, least i got all weekend to furk with it.


peese

-me

---

### Post by carnauth on 2009-03-28
No ideas anyone???


What is the diff between M$ and Ubuntu when it comes to Samba>? It lets me print from my other Ubuntu box, xp no.. When I browse to other pc via smb:\\*host* it makes me log in to the workgroup using the local account from say BoxB. But the login ID from BoxB dosent exist on BoxA(print server)

Repeating above.. I have it set to allow all.. 
 
I dont have users setup specifically for smb on BoxA, but when BoxB logs on I have to put in local password from BoxB's users. I dont have to use PW's to login to workgroup from XP. If its set to allow all how come it blocks xp only and likes ubuntu. The file shares work fine, can access all my data fine from  anywhere. It seems that I cant print to BoxA unless I login when I browse the Workgroup(something ubuntu makes me do that win dosen't).. I know the account on BoxB dosen't exist on BoxA. I think it handles smb diff than windoze. I dont know what kind of creds it presents when I try to print from xp if its loggin' on workgroup as user@xpmachine or just anonymously browsing.


Whats wrong with this picture?



Feelin' even dumber!

-me

---

### Post by carnauth on 2009-03-29
Whoohoooo!!!


Like  I had said earlier it had to be something simple. 
It  was hidden somewhere in the smb.conf (its'a meee Maariioooo!)lol- NEway_ therr were two lines i had to change from no to yes. simple really.. I was thinkin that when I switched it to              "Allow printing from everyone except thes users."
That should have been everyone right.?. .

nope #-o

It still set up the printer section as "guest ok = no"


Fixed 

I figured that it would have set it through the new guisince all recent posts i found that the user was using intrepid were abandoned without input. (kinda like here)[-Xshame shame.. . I saw lots of samba setup guides but nothign for intrepid. all had difrerent user interfaces so i figured that they would handle the sitch differently. not to mention maybe samba was tweaked a bit using a three year old howto might have caused some problems for me ... 

so all in all ... simple setup 

Printer properties clikc on shared and accepting jobs. go to policies make sure all network pcs that would be using the printer are either on the list of accepted or that it is set to allow all. close printer properties

Go to server settings  and chek Publish shared printers connected to this machine

bing bang boom almost done open up samba conf...  find your printer section and make sure that "guest ok" is set to yes.. under both the print and driver sections.

So if you go allow all and dont have to type in allowed users you are looking at what 2 clicks to printing two more for properties one click to policies chek chek one more to access control click allow click OK. 7 clicks so far. click server again for settings one more for publish then click ok. 
Gui side setup is done in what ten mouse clicks counting the right clicks.how long does it take you to click your mouse 10 times... not long. I mean if ur slow, what 30 seconds... 
  
Thats where i was ..when i made this post. All i needed other than clicking the check box'z in the printer cofig. All that you need to have fully open access is to chane two values.

now alt+F2 gksudo gedit /etc/samba/smb.conf 
find section with printers and print drivers i belive [printers] and [print$]highlight no type yes do it again and boom your  ready to use it from windoze pcs. 

Since you are only changing two words not adding anyoptions that may or may not be understood, i feel pretty safe to not even make a backup in this situation.. just saying if you think you broke it you only gotta change yes back to no.(hopefully we could all do that without help)
so total setup time to have printer openly shared is about 30 seconds to `bout a min and a half...




peese


-me


PS  Can i close my own thread or does it have to be done by mod..  Already changed the title to (Solved) guess its not automated... ..

---

