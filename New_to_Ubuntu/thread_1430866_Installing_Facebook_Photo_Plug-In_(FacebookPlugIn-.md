---
title: "Installing Facebook Photo Plug-In (FacebookPlugIn-1.0.3.tar.gz)"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by Autumn7 on 2010-03-15
I am trying to install the Facebook photo Plugin and can not seem to access it.      Please note I just switched yesterday from Windows XP to Ubuntu, so I am just getting used to it.    The downloaded file is named &quot;FacebookPlugIn-1.0.3.tar.gz&quot;     I have tried opening:  FacebookPlugIn1.0.3.tar.gz/FacebookPlugin_Install.sh     but it opens as a read-only file And I tried opening  FacebookPlugIn-1.0.3.tar.gz/libnfbook_1_0_3.so  but nothing happens. Also I have tried to follow the solutions for similar problems posted in earlier forms including creating a new file in home/user/.mozilla/plugin and extracting file &quot;libnfbook_1_0_3.so&quot; to this location, but it did not work. Perhaps this is a slighly updated facebook plugin.     Please Help! Any Solutions/Information would be really appreciated.

---

### Post by puzzler995 on 2010-03-15
do:
```
sudo chmod a+x FacebookPlugin_Install.sh
``` and let me know if it works then.

---

### Post by Autumn7 on 2010-03-15
Thankyou for replying. I tried entering :
sudo chmod a+x FacebookPlugin_Install.sh
But it keeps saying:
chmod: cannot access `FacebookPlugin_Install.sh': No such file or directory

---

### Post by tad1073 on 2010-03-15
Are you in the directory that you saved the file in?

---

### Post by Autumn7 on 2010-03-15
I think so. I have the file saved to my desktop. Also copied the file to home/user/.mozilla/plugin.

---

### Post by lavinog on 2010-03-15
Where did you get this plugin from?

---

### Post by Autumn7 on 2010-03-15
I was trying to post multiple photos on Facebook. I clicked on "Create an Album with many photos". Then a pop-up window opened stating: "The Facebook Plug-in is required to upload photos. Please install it now." And I clicked on "Install" and "download facebook plugin"

---

### Post by xfearxnxloathing on 2010-03-16
> **puzzler995 said:**
> do:
```
sudo chmod a+x FacebookPlugin_Install.sh
``` and let me know if it works then.

this does not work.  im using google chrome for ubuntu and was on facebook today and had the same problem.  this is a new plugin that facebook is asking specifically linux users to download and install.  the file name is: FacebookPlugIn-1.0.3.tar.gz

i am navigated to the correct directory with root privs, thnx!

---

### Post by Autumn7 on 2010-03-16
> **xfearxnxloathing said:**
> this does not work.  im using google chrome for ubuntu and was on facebook today and had the same problem.  this is a new plugin that facebook is asking specifically linux users to download and install.  the file name is: FacebookPlugIn-1.0.3.tar.gz

i am navigated to the correct directory with root privs, thnx!

Do I enter root "privs" into the terminal? ...sorry I am really not good with this stuff yet.

---

### Post by xfearxnxloathing on 2010-03-16
> **Autumn7 said:**
> Do I enter root "privs" into the terminal? ...sorry I am really not good with this stuff yet.

to get root privileges in terminal just type sudo before the rest of the command then you are prompted for the root password (that you setup)


examples: 

-to navigate to the directory that google chrome downloaded the file to-
nV@Elemented:~$ [COLOR="Red"]cd[/COLOR] /home/envy/Downloads/

-for root-
nV@Elemented:~$ [COLOR="Red"]sudo[/COLOR] chmod a+x Facebook.shblahblah

---

### Post by Autumn7 on 2010-03-16
> **xfearxnxloathing said:**
> to get root privileges in terminal just type sudo before the rest of the command then you are prompted for the root password (that you setup)

Thanks. I seem to be ok with that but do I enter privs along with the code: 
sudo chmod a+x FacebookPlugin_Install.sh

I will try downloading google chrome.

---

### Post by overlord.gaurav on 2010-03-16
> **xfearxnxloathing said:**
> this does not work.  im using google chrome for ubuntu and was on facebook today and had the same problem.  this is a new plugin that facebook is asking specifically linux users to download and install.  the file name is: FacebookPlugIn-1.0.3.tar.gz

i am navigated to the correct directory with root privs, thnx!
Once you have done sudo chmod a+x FacebookPlugin_Install.sh do:
```

sh FacebookPlugin_Install.sh

```
> **Autumn7 said:**
> Thanks. I seem to be ok with that but do I enter privs along with the code: 
sudo chmod a+x FacebookPlugin_Install.sh

I will try downloading google chrome.

No. The guy meant he has navigated with root privileges.
Navigate to the directory and do:
```

sudo chmod a+x FacebookPlugin_Install.sh
sh FacebookPlugin_Install.sh

```

---

### Post by xfearxnxloathing on 2010-03-16
> **overlord.gaurav said:**
> Once you have done sudo chmod a+x FacebookPlugin_Install.sh do:
```

sh FacebookPlugin_Install.sh

```


No. The guy meant he has navigated with root privileges.
Navigate to the directory and do:
```

sudo chmod a+x FacebookPlugin_Install.sh
sh FacebookPlugin_Install.sh

```

 **.sh** isnt working for me, i have **[COLOR="Red"]tar.gz[/COLOR]**

---

### Post by overlord.gaurav on 2010-03-16
First uncompress the file. You can simply right click and select extract here, or open a terminal and navigate to the directory where the .tar.gz file is and then type:
```

tar zxf FacebookPlugin_Install.tar.gz

```
Then do the following:
```

sudo chmod a+x FacebookPlugin_Install.sh
sh FacebookPlugin_Install.sh

```

---

### Post by qwerty2009 on 2010-03-16
the facebook plugin is allready pre-installed you just have to enable it in F-Spot, to do this open f-spot,

click on "edit" from the menu bar
select "manage extensions" 
expend the "export" option
enable the facebook plugin

you can then simply ctrl-click multiple images then select "photo" from the menu bar and then "export to" > "Facebook"

---

### Post by lidex on 2010-03-16
After downloading, right-click on tar.gz file and select "Extract Here" then follow previous instructions using filename ending in .sh exactly as it appears.

---

### Post by overlord.gaurav on 2010-03-16
Alright. I tried to install the plug-in for myself as I use facebook too.
I did the steps I mentioned. The .tar.gz filename is different though. Filename is 'FacebookPlugIn-1.0.3.tar.gz'. I downloaded the file, moved it to Documents and then did:
```

cd Documents
tar zxf FacebookPlugIn-1.0.3.tar.gz
cd FacebookPlugIn-1.0.3
sudo chmod a+x FacebookPlugIn_Install.sh
sh FacebookPlugIn_Install.sh

```
You'll get the output saying: Copying libnpfbook_1_0_3.so to /home/username/.mozilla/plugins/libnpfbook_1_0_

This is what the script is meant for. The script works fine.
However, there is another twist in the tale. The plug-in isn't working for ubuntu users. The older version was working but the newer version isn't.
Look at this [page]("http://www.facebook.com/topic.php?uid=184826119663&topic=11603#!/topic.php?uid=184826119663&topic=12994").

---

### Post by Autumn7 on 2010-03-16
Have tried both ".sh" and" tar.gz" after extracting the files but still no luck.

---

### Post by Autumn7 on 2010-03-16
> **overlord.gaurav said:**
> Alright. I tried to install the plug-in for myself as I use facebook too.
I did the steps I mentioned. The .tar.gz filename is different though. Filename is 'FacebookPlugIn-1.0.3.tar.gz'. I downloaded the file, moved it to Documents and then did:
```

cd Documents
tar zxf FacebookPlugIn-1.0.3.tar.gz
cd FacebookPlugIn-1.0.3
sudo chmod a+x FacebookPlugIn_Install.sh
sh FacebookPlugIn_Install.sh

```You'll get the output saying: Copying libnpfbook_1_0_3.so to /home/username/.mozilla/plugins/libnpfbook_1_0_

This is what the script is meant for. The script works fine.
However, there is another twist in the tale. The plug-in isn't working for ubuntu users. The older version was working but the newer version isn't.
Look at this [page]("http://www.facebook.com/topic.php?uid=184826119663&topic=11603#%21/topic.php?uid=184826119663&topic=12994").


ah, Thank you! I have wasted much time trying to figure this out..but at least now I know it's not just because of my lack of ubuntu experience.
I think I will try to install a pre-9.4 Version of ubuntu tommorrow to see if that works.
Thank you to all for trying to help, I might have spent the next couple days reading through ubuntu manuels if not for your help :-)

---

### Post by overlord.gaurav on 2010-03-16
> **Autumn7 said:**
> Have tried both ".sh" and" tar.gz" after extracting the files but still no luck.

Copy the downloaded file(FacebookPlugIn-1.0.3.tar.gz) to Documents folder and to the steps mentioned in my previous post.

Even when you insatll the plug-in it will not work. Look at the discussion [here]("http://www.facebook.com/topic.php?uid=184826119663&topic=12994").

*Edit: Aah, you beat me to it.
Anyway, you're welcome.

PS: I also looked for v1.0.1, it can be downloaded from [here]("http://www.facebook.com/fbplugin/linux-x86/install/FacebookPlugIn-1.0.1.tar.gz").
You can install this plug-in but it doesn't help either. Facebook says you have to update or use the simple photo uploader.
Probably all we can do is wait for a fix.

---

### Post by Autumn7 on 2010-03-16
> **overlord.gaurav said:**
> Copy the downloaded file(FacebookPlugIn-1.0.3.tar.gz) to Documents folder and to the steps mentioned in my previous post.

Even when you insatll the plug-in it will not work. Look at the discussion [here]("http://www.facebook.com/topic.php?uid=184826119663&topic=12994").

*Edit: Aah, you beat me to it.
Anyway, you're welcome.

PS: I also looked for v1.0.1, it can be downloaded from [here]("http://www.facebook.com/fbplugin/linux-x86/install/FacebookPlugIn-1.0.1.tar.gz").
You can install this plug-in but it doesn't help either. Facebook says you have to update or use the simple photo uploader.
Probably all we can do is wait for a fix.


Darn facebook. I am using ubuntu 9.10 but according to [nevabry]("http://ubuntuforums.org/member.php?u=772943")  (quoted from january 20th) the advanced photo uploader "worked fine before my Upgrade to Ubuntu 9.04, and now it doesnt." He/She is refering to "FacebookPlugIn-1.0.0.tar.gz"   but I still might try installing an earler version of unbuntu tommorrow to see if the new facebook advanced uploader is compatible with it....that is if my patience is restored by tommorow...;-) I've had enough of this for one day. Thanks again.

---

### Post by overlord.gaurav on 2010-03-16
> **Autumn7 said:**
> Darn facebook. I am using ubuntu 9.10 but according to [nevabry]("http://ubuntuforums.org/member.php?u=772943")  (quoted from january 20th) the advanced photo uploader "worked fine before my Upgrade to Ubuntu 9.04, and now it doesnt." He/She is refering to "FacebookPlugIn-1.0.0.tar.gz"   but I still might try installing an earler version of unbuntu tommorrow to see if the new facebook advanced uploader is compatible with it....that is if my patience is restored by tommorow...;-) I've had enough of this for one day. Thanks again.

I don't think going back to a previous version of ubuntu will help because Facebook will ask you to install its latest plug-in..which isn't working.
Do inform us if you get it to work!

---

### Post by rafita on 2010-03-16
In case it is of any use: the Shotwell photo manager was updated  recently, and has support for uploading to facebook (f-spot does not work for me)

---

### Post by xfearxnxloathing on 2010-03-18
> **qwerty2009 said:**
> the facebook plugin is allready pre-installed you just have to enable it in F-Spot, to do this open f-spot,

click on "edit" from the menu bar
select "manage extensions" 
expend the "export" option
enable the facebook plugin

you can then simply ctrl-click multiple images then select "photo" from the menu bar and then "export to" > "Facebook"

worked for me, thnx.

---

### Post by Autumn7 on 2010-03-18
> **qwerty2009 said:**
> the facebook plugin is allready pre-installed you just have to enable it in F-Spot, to do this open f-spot,

click on "edit" from the menu bar
select "manage extensions" 
expend the "export" option
enable the facebook plugin

you can then simply ctrl-click multiple images then select "photo" from the menu bar and then "export to" > "Facebook"

Yes, thank-you. This does work for me as well. Now I am able to upload multiple photos to facebook from my computer. However I am still not able to post multiple photos in one post. I guess I will have to wait for a facebook fix on this.

---

### Post by rossmoore on 2010-04-01
FireUploader is a useful plugin for Firefox to help you achieve similar things. Its interface is very like FireFTP (same people?).

---

### Post by sevenX on 2010-04-09
Is there a fix for this yet?  F-Spot does not work for me, it freezes when logging in... I posted a thread on it but got no feedback.  Hope someone posts here when the plugin is fixed for us...

---

### Post by lavinog on 2010-04-09
> **sevenX said:**
> Is there a fix for this yet?  F-Spot does not work for me, it freezes when logging in... I posted a thread on it but got no feedback.  Hope someone posts here when the plugin is fixed for us...

It is not going to get fixed in 9.10 most likely, you might want to try it in 10.04 (see if it works with beta2 live)

---

### Post by Autumn7 on 2010-04-09
> **sevenX said:**
> Is there a fix for this yet?  F-Spot does not work for me, it freezes when logging in... I posted a thread on it but got no feedback.  Hope someone posts here when the plugin is fixed for us...

Have you tried using F-spot or FireUploader? 

_F-Spot:_   Open F-spot (should already be installed) > Go to edit> select "manage extensions"> export> enable facebook plugin> then select photos (ctrl-click for multiple photos)> select "photo" from the menu bar> "export to" > facebook.


_FireUploader:_ Go to Tools>Add-ons>Get Add-ons> then search for fireuploader. Or just go to [www.fireuploader.com]("http://ubuntuforums.org/www.fireuploader.com") and download the plugin.

Someone has also suggested the shotwell photo uploader and the bloom photo uploader, but I have not tried either. 

Shotwell : (not sure of address)
Bloom: [http://www.facebook.com/apps/application.php?id=2330519541](http://www.facebook.com/apps/application.php?id=2330519541)

---

### Post by trestevenson on 2010-04-12
It's pretty disappointing that Facebook hasn't gotten their sh*t together regarding this plugin.  Ultimately, I had to resort to using F-spot in order to batch-upload my photos.  I didn't have any problems doing it this way though, and I'll probably continue to do so in the future.  I hadn't had any experience with the program before today, but the functionality is pretty good.  It certainly beats having to upload only four pictures at a time via the Facebook website.  Thanks for the info guys!  It's certainly helped me out!

---

