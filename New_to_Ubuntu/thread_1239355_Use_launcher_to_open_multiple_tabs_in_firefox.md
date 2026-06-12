---
title: "Use launcher to open multiple tabs in firefox?"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by MattM11 on 2009-08-13
Is it possible to create a launcher on the desktop that will open multiple saved tabs in Firefox? So, for example, I could create a launcher that, when clicked, would open up several saved tabs on a particular topic?

---

### Post by VCoolio on 2009-08-13
In firefox: edit > preferences > main > tabs check "open new windows in new tabs instead"

Now make a launcher with as command "firefox [http://url1.com](http://url1.com) & firefox http://url2.com"

or write a script in gedit and save as .sh if you use long or many urls:

#!/bin/sh
firefox [http://url1.com](http://url1.com) & 
firefox [http://url2.com](http://url2.com) &
firefox [http://url3.com](http://url3.com) &

Then make the launcher command: sh /path/to/script.sh

---

### Post by MattM11 on 2009-08-13
Excellent.

The .sh stuff looked a bit too adventurous for a newbie like myself, but the launcher command worked a treat. 

Thanks.

---

### Post by Hachi-Roku on 2009-10-02
ah ha!!! after much searching and googling all i needed was some &'s for my script to work.

jeez i wish i found this thread first. would of saved much trial and error.

all good though, i learned some things along the way.

Thanks VCoolio

---

### Post by HarrisonNapper on 2009-10-02
Also note that firefox has this functionality built in. Go to Edit>Preferences and put multiple addresses in your "Home Page" field separated by carriage returns and that should have the same effect.

---

### Post by Hachi-Roku on 2009-10-02
Yeah i semi take that back....
it seems firefox needs to be open for it to work.
otherwise i get the 'firefox is already running but not responding-....blah blah'

got some crazy 20 windows trying to open. nasty

---

### Post by ikt on 2009-10-02
> **Hachi-Roku said:**
> Yeah i semi take that back....
it seems firefox needs to be open for it to work.
otherwise i get the 'firefox is already running but not responding-....blah blah'

got some crazy 20 windows trying to open. nasty

Do you want to have 4 windows you'd like to open every time or are you trying to have like 10 firefox icons on the launcher which depending on what you are wanting to see, opens up 4+ different tabs for each point of interest?

---

### Post by Hachi-Roku on 2009-10-02
hmmm biiiit of both.

Just writing a shell script to open about 20 sites when i double click on the launcher.

I dont want these all the time, every time. Just on demand.

Thinking of trying a launcher to open firefox then run the script... may work.

Or is there a command to pause the script for a few seconds?
... i tried to open firefox by itself first in the script, but then the script stopped there and didnt see the rest of the code.

maybe its just easier if i post the code yeah?

I put the first few in quotes as the & in the url was seemingly playing tricks.


```
    #!/bin/sh


firefox "http://www.swellnet.com.au/loc_report.php?region_id=19&state_id=4" &
firefox "http://www.swellnet.com.au/forecast.php?state_id=4&region_id=19" &
firefox "http://www.swellnet.com.au/forecast.php?region_id=22&state_id=4" &
firefox "http://www.swellnet.com.au/loc_report.php?state_id=4&region_id=22" &
firefox http://www.windfinder.com/forecast/noarlunga &
firefox http://www.windfinder.com/forecast/victor_harbor &
firefox http://www.surfsouthoz.com/ &
firefox http://www.bom.gov.au/jsp/marine/wind/index.jsp &
firefox http://www.bom.gov.au/products/IDS60901/IDS60901.95811.shtml &
firefox http://www.bom.gov.au/products/IDS60901/IDS60901.94808.shtml &
firefox http://magicseaweed.com/Seaford-Surf-Report/532/ &
firefox http://www.bom.gov.au/products/IDS65030.shtml &
firefox http://www.bom.gov.au/oceanography/tides/MAPS/sagulf.shtml#map &
```

---

### Post by Hachi-Roku on 2009-10-02
The above works if FF is already open. Goes crazy if its not.

---

### Post by Paddy Landau on 2009-10-02
Put the tabs all on the same line, thus:
```
firefox http://www.ubuntu.com/ http://ubuntuforums.org http://www.playonlinux.com/ http://ubuntuforums.org/forumdisplay.php?f=243
```

---

### Post by VCoolio on 2009-10-02
maybe it helps if you give it a break after the first url?

firefox [http://url1](http://url1) &
sleep 10; 
firefox [http://url2](http://url2) &
etc.etc.

---

### Post by Paddy Landau on 2009-10-02
> **VCoolio said:**
> maybe it helps if you give it a break after the first url?
See [post 10]("http://ubuntuforums.org/showthread.php?p=8040017#post8040017").

---

### Post by Hachi-Roku on 2009-10-04
Thanks Paddy that worked.
I tried it once before, but with carriage returns not a whitespace, and that didnt work.

Works now with just a whitespace.
Any idea why returns dont work? makes the code alot neater.

Thanks!

---

### Post by Paddy Landau on 2009-10-04
> **Hachi-Roku said:**
> Any idea why returns dont work? makes the code alot neater.
A return indicates the end of the command. If you want to use returns, you'll have to use the backslash.

So, the following indicates three separate commands, with the second and third not being understood.
```
firefox http://www.ubuntu.com/
        http://ubuntuforums.org
        http://www.playonlinux.com/
```Whereas the backslashes in the following example tell bash that it's all one command.
```
firefox http://www.ubuntu.com/       \
        http://ubuntuforums.org      \
        http://www.playonlinux.com/
```HTH

---

