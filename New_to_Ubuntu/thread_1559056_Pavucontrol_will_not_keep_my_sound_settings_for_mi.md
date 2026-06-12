---
title: "Pavucontrol will not keep my sound settings for microphone [acer aspire 4810T]"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by rs87424 on 2010-08-23
I was using google talk and skype and I noticed there was no sound being input into the microphone which is internal for my computer.  I then looked into pavucontrol and went to the volume bar for the microphone and put one to 100% and the other to 0% because that usually helps keep them from canceling out and keeping quiet for some odd reason.  but every time I close the application it still goes back to the original settings and I clicked the button off that usually makes the two volume bars stick together which was causing the problem in the first place.. how can I make pavucontrol save the settings so I don't have to keep coming back to fix this simple problem

---

### Post by dillzz on 2010-10-20
rs87424,

I am having the same issue. I however am running Kubuntu 10.10 and had to install pavucontrol in order to get my USB mic/headset to be recognized.  It works fine through flash/google talk when I manually make the setting, but as soon as I close the browser and re-open it resets pulse back to my speakers, quite frustrating....

---

### Post by empty_spaces on 2010-10-21
> **rs87424 said:**
> I was using google talk and skype and I noticed there was no sound being input into the microphone which is internal for my computer.  I then looked into pavucontrol and went to the volume bar for the microphone and put one to 100% and the other to 0% because that usually helps keep them from canceling out and keeping quiet for some odd reason.  but every time I close the application it still goes back to the original settings and I clicked the button off that usually makes the two volume bars stick together which was causing the problem in the first place.. how can I make pavucontrol save the settings so I don't have to keep coming back to fix this simple problem

There should be a check mark to save your settings, next to the slider lock button.
Moving the sliders automatically unchecks the check mark, so click it _once_ after you set your slider positions.

---

### Post by empty_spaces on 2010-10-21
And if the above doesn't work, make sure you have unchecked the option in skype to automatically adjust audio levels.

---

### Post by dillzz on 2010-10-22
empty_spaces,

Thanks for the information, I will try that.  Won't that just save the volume level?  I am looking to save what soundcard it uses as the output.  I have to keep changing it cause it blasts through my sound card and not usb headset.  

Thanks,


Dillzz

---

### Post by dillzz on 2010-10-23
Ok I checked this, and I do not have a checkbox to save settings.  I attached a screenshot. ..  See how it defaults to my sound blaster audigy instead of my headset for google talk.  Even If I change the setting and initiate a new call, it defaults back.

---

### Post by empty_spaces on 2010-10-23
The checkmarks to save the settings are on the "output devices" and "input devices" tabs (See 2nd screenshot of input tab).
Here are a couple of screenshots from my netbook running Ubuntu 10.10 (Gnome)
Maybe Google Talk has some setting which alters the system settings.

---

### Post by jamisonaw on 2010-10-25
I'm having the same problem. 

While Skype, Gizmo and Gmail/Settings/Chat Verification page are closed, I've zero'd out the left channel using pavucontrol and clicked the "Lock" button. 

Opening Skype and making a test call works fine, because I unchecked the "Allow Skype to automatically adjust my mixer levels."

Opening -Gmail/Settings/Chat Verification page resets the left channel within seconds. **The lock button is still checked, but now the channels are moving together.**

The Google Talk plugin shows up on the recording tab of pavucontrol and two inputs (see attached screenshot).

As far as I can tell, there's no way to stop the Talk plugin from changing the volumes. Any suggestions?

I'm using and Acer Aspire Netbook D255-N558Qcc with Ubuntu 10.10 gnome.

Thanks in advance.

---

### Post by banker247 on 2010-11-09
any idea which file pavucontrol uses to access saved settings upon launch?

---

### Post by rs87424 on 2010-11-18
I am not sure why google talk keeps making the pavucontrol settings change.  So I guess using skype works... but pavucontrol microphone settings keep changing with skype as well... its a really frustrating problem...any help would be much appreciated

---

### Post by rs87424 on 2010-11-18
and I have unchecked the skype allows auto box as well.  I cannot use google talk because apparently that is causing most of the problems...

---

### Post by viren22 on 2010-12-16
I have same problem on my acer aspire one D255. Google talk will dynamically change the settings on microphone channels even if you don't want it to do so..Did anyone find any solution that works?

Update..12/16/2010.. Found a solution for this problem
To turn off autoadjust by google talIk plugin:
     cd ~/.config/google-googletalkplugin    # get to google chat's directory
      cp -p options options.bak        # make a backup before changing stuff..
      gedit options                # edit the config file
If you don't have file named options in this folder create one..
Add following line to this file..
      audio-flags=1
      Save and close the file.
Close and open your browser and try making a audio call..it should work now..

---

### Post by Mediosordo on 2011-12-08
It works!! (on an Aspire One ZG5)

Many many thanks!

---

