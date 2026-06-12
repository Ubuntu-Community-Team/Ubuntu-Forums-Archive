---
title: "dual booting"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by drgcpatel on 2010-06-07
I am using Ubuntu 10.04 on my laptop. I have to use the website [http://www.amway.ca/EN](http://www.amway.ca/EN) for my business  purpose to show and watch videos and listen to audio files for learning  the business and informations. As it uses only Silverlight, I was  directed to install Moonlight which I did but still could not succeed to  see or listen.
I contacted the customers services at the amway's   head office in USA and had a talk with a representative. They are  currently not supporting Linux but are trying to find a solution for  this.
My question now is that is there anyone who can help me with a  solution to this or help me to set up a dual booting system as I like to  use Ubuntu but am forced to install Windows for my business purpose or I  have to switch back to Windows only?
If the suggestion is for dual  booting please help me with how to do that and oblige.
thanks,
dr.gaurang

---

### Post by Scunizi on 2010-06-07
If you're getting video but no audio you might have some missing codecs for the audio.  gstreamer-plugins-ugly might solve the problem.. search synaptic package manager for gstreamer and install -ugly then try again and see what happens.

---

### Post by Mariane on 2010-06-07
I can watch the presentation video on the first page, using seamonkey with flash pluggin. 

Can you watch this animation? If yes, can you give me a link to one of the videos which you cannot watch? 

("install -ugly"? Is there really such a command? ROTFL!)

Mariane

---

### Post by Scunizi on 2010-06-07
yep.. they are actually called gstreamer0.10-plugins-ugly-multiverse and have codecs that might pose distribution problems in some countries because of copyright issues..

---

### Post by drgcpatel on 2010-06-07
> **Mariane said:**
> I can watch the presentation video on the first page, using seamonkey with flash pluggin. 

Can you watch this animation? If yes, can you give me a link to one of the videos which you cannot watch? 

("install -ugly"? Is there really such a command? ROTFL!)

Mariane


Thanks Mariane
I did install gstream - ugly as said but unsuccessful to view the file. I am giving the link of videos I want to watch so that you can help me further. [http://www.amway.ca/Shop/Search/SearchResults.aspx?searchkeyword=videos](http://www.amway.ca/Shop/Search/SearchResults.aspx?searchkeyword=videos)

Hoping to get more help to succeed.

dr.gaurang

---

### Post by Matt__ on 2010-06-07
did you install the moonlight preview version 3?
I just installed this, attempted to play the ribbon consumer video and was prompted for a plugin...accepted and video runs fine, including sound.

Mind you firefox froze up for a few seconds once the video ended


// edit: further testing and firefox may freeze totally and need to be force quit. this may sound like a rant but any company that insists on using solely sivlerlight (buggy piece of junk dosnt work well on my windows install either) needs shooting! havnt they heard of accessibility? :P

---

### Post by Scunizi on 2010-06-07
Check out that site's "Validate" line.. it's looking to validate against Windows and IE7.. They are using MS Sharepoint etc.. 

Looks like they were sold a bill of goods as they say.. If Amway is attempting a global presence then their consultants should have let them know other parts of the civilized world are looking for universal access, not propitiatory.

> <head id="ctl01_Head1"><meta name="msvalidate.01" content="4BF667B162E62AE3D0B0436EF4F0BD92" /><meta name="verify-v1" content="P7zZjV9ChWtB4EAiMqFfZpuX/ZOK1JrCBp7CDYVq18Q=" /><meta name="ROBOTS" content="NOODP" /><meta name="GENERATOR" content="Microsoft SharePoint" /><meta http-equiv="X-UA-Compatible" content="IE=EmulateIE7" /><meta http-equiv="Expires" content="0" /><title>


---

