---
title: "How to open  X- Shockwave-flash object"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Peterfc on 2009-07-26
Hi Guys

I have been trying to view property on a property website. The image says.

Dscn9532_out.swf(application/X-shockwave-flash object) This means nothing to me i am totally lost. 

Thanks for reading this thread. 

Property_images/213/pan/DSCN9532_out.swf

---

### Post by okey666 on 2009-07-26
Do you have flash installed? Could you give us a link to the webpage?

---

### Post by Peterfc on 2009-07-26
Hi Okey666

On the page it says that Adobe 9 is required. I have Adobe 9 installed.

If you go down the page ubder where it says about Adobe 9 their is three Panorama links. When i click the link it opens in a new windows but the window is blank.  

Thanks
 

[http://www.goisproperty.com/Property_Central_Portugal/Property-en-213.html](http://www.goisproperty.com/Property_Central_Portugal/Property-en-213.html)

---

### Post by Michus on 2009-07-26
I have this issue too. 
I installed ubuntu (jaunty) 3 days ago and am a very new user. 
But like what I see :)
I would really like not to have to dual boot windows and solely run ubuntu but Mozilla doesnt run several key animated websites for me:

club penguin (v important!)
[http://www.clubpenguin.com/](http://www.clubpenguin.com/)

carter jonas estate agents 
[http://www.carterjonas.co.uk/buy/buy-residential-property.aspx](http://www.carterjonas.co.uk/buy/buy-residential-property.aspx)

I have adobe flash 9.0.999.0 installed

Is it me or them?:confused:

---

### Post by Liolikas on 2009-07-26
I have Firefox 3.0.x and Flash 10.x and both pages work.
I think try to update to Flash 10.

---

### Post by Michael.Godawski on 2009-07-26
> **Liolikas said:**
> I have Firefox 3.0.x and Flash 10.x and both pages work.
I think try to update to Flash 10.

I second that. Upgrading Flash might help.

[LIST]
[*][http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
[/LIST]

---

### Post by okey666 on 2009-07-26
Seems to work for me, I have 9.04 64-bit with flash 10 using firefox.

On 9.04 run this and it should upgrade you:
```
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-installer
```

Thats what I use on 64-bit and I think it will work on 32-bit as well.

---

### Post by Michus on 2009-07-26
Thanks guys. I am sure that this is the right thing to do.

I have tried to install Flash 10 - it is listed as enabled in Mozilla plug ins , as in Flash v9.
It is not working.
Any ideas?
I will try to upgrade firefox to 3.5 and reinstall Flash 10

---

### Post by Liolikas on 2009-07-26
You have 64 bit system?

---

### Post by Michus on 2009-07-26
It has an Intel Atom 330 processor
[http://processorfinder.intel.com/details.aspx?sSpec=SLG9Y](http://processorfinder.intel.com/details.aspx?sSpec=SLG9Y)

Is that a 64 bit, I cant see it in its product specifications?

---

### Post by okey666 on 2009-07-26
Run
```
uname -a
```

---

