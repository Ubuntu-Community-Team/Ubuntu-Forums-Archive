---
title: "Software center and update not working"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by KhensuRA on 2010-10-24
Not sure what I did, but I can no longer get into the software center nor can I update. When I click on the ubuntu software center nothing happens and when try to update, the manager opens up and then ask me to close the program. I have restarted several times but run to the same issues. I just updated to 10.10 and all was well for a week or so then this has happened. Thanks in advance..

---

### Post by KhensuRA on 2010-10-24
Forgot to add that everything else seems to be working just fine. I am able to get online, etc.

---

### Post by wojox on 2010-10-24
What happens when you open your terminal and run

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by KhensuRA on 2010-10-24
This is what I get when i try using the code you gave me in the terminal.

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by KhensuRA on 2010-10-25
Any ideas? I have tried all that is within my knowledge. Please let me know if anymore information is needed.

---

### Post by wojox on 2010-10-26
Go to System > Administration > Software Sources and get uncheck the Medibuntu repo's and try again.

---

### Post by philinux on 2010-10-26
> **KhensuRA said:**
> This is what I get when i try using the code you gave me in the terminal.

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Run this and post back.

```
cat /etc/apt/sources.list.d/medibuntu.list

```

---

### Post by KhensuRA on 2010-10-28
Wojox, Thanks for the reply but I am not seeing the settings that you posted up. When I go into Admin, I do not see software settings. Hmmm


philinux, ran what you asked and here it is...

```
irgl@PachecosPuter:~$ cat /etc/apt/sources.list.d/medibuntu.list
  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "DTD/xhtml1-strict.dtd">
                <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
                <head>
                    <title>Medibuntu :: Multimedia, Entertainment &amp; Distractions In Ubuntu</title>
                    <meta http-equiv="Content-Type" content="text/xhtml+xml; charset=utf-8" />
                    <link rel="stylesheet" href="medibuntu.css" type="text/css" />
                </head>
                    <body>
                        <div id="headerbloc">
                        <div id="header">
                            <h1><span class="hidden">Medibuntu<br />Multimedia, Entertainment &amp; Distractions In Ubuntu</span></h1>
                        </div>
			<div id="google">
				<script type="text/javascript"><!--
				google_ad_client = "pub-8132065110046054";
				/* Medibuntu */
				google_ad_slot = "3283366330";
				google_ad_width = 180;
				google_ad_height = 170;
				//-->
				</script>
				<script type="text/javascript"
				src="http://pagead2.googlesyndication.com/pagead/show_ads.js">
				</script>
			</div>
                        </div>
                        <ul id="menu"><li><a href="index.php">Presentation</a></li>
                        <li><a href="http://help.ubuntu.com/community/Medibuntu">Repository Howto</a></li>
                        <li><a href="http://packages.medibuntu.org/">Packages</a></li>
                        <li><a href="contact.php">Contact us</a></li>
                                 </ul>
        <div id="page">
              <h2>Presentation</h2>
                                <p>
                                    <strong>
                                        Medibuntu (Multimedia, Entertainment &amp; Distractions In Ubuntu) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc).
                                    </strong>
                                </p>
                                <p>
                                    Medibuntu is a packaging project dedicated to distributing software that cannot be included in Ubuntu for various reasons, related to geographical variations in legislation regarding intellectual property, security and other issues:
                                </p>
                                <ul>
                                    <li>patentability of software, algorithms, formats and other abstract creation</li>
                                    <li>legal restrictions on freedom of speech or communication</li>
                                    <li>restrictions on the use of certain types of technical solution, such as cryptography</li>
                                    <li>legal restrictions on imports of software technology, requiring for example specific permissions</li>
                                    <li>etc.</li>
                                </ul>
                                <p>
                                    A lot of excellent <a href="http://www.fsf.org/licensing/essays/free-sw.html">free software</a> and non-free software is affected by such restriction somewhere in the world, thus preventing its inclusion into Ubuntu that, for economy and simplicity, are generally identical for all countries.
                                </p>
                                <p>
                                    We refuse to resign ourselves to abandoning software that may be legally useful somewhere, and we have chosen to provide it with professional quality packaging, easily usable within the context of Ubuntu.<br />
                                    This repository provides packages for Ubuntu distribution.
                                </p>
                                <p>
                                    It is your legal responsibility to make sure that the software you are installing can be legally used in your country and for your intended purpose.
                                </p>
                                        </div>
          <div id="paypal"><form action="https://www.paypal.com/cgi-bin/webscr" method="post">
<p>
<input type="hidden" name="cmd" value="_xclick" />
<input type="hidden" name="business" value="maxenced@gmail.com" />
<input type="hidden" name="item_name" value="Medibuntu" />
<input type="hidden" name="no_shipping" value="0" />
<input type="hidden" name="no_note" value="1" />
<input type="hidden" name="currency_code" value="EUR" />
<input type="hidden" name="lc" value="US" />
<input type="hidden" name="tax" value="0" />
<input type="hidden" name="bn" value="PP-DonationsBF" />
<input type="image" src="https://www.paypal.com/en_US/i/btn/x-click-but04.gif" name="submit" alt="Effectuez vos paiements via PayPal : une solution rapide, gratuite et sécurisée" />
<img alt="" src="https://www.paypal.com/en_US/i/scr/pixel.gif" width="1" height="1" />
</p>
</form>
          </div>
                        <div id="footer">:: designed by <a rel="nofollow" href="http://www.most-enchained.com">_Enchained</a> - logo by <a rel="nofollow" href="http://www.racoon97.net">racoon97</a> - Domain by <a rel="nofollow" href="http://flosoft.biz">Flosoft</a>  - Managed by <a rel="nofollow" href="http://www.dunnewind.net">Sp4rKy</a> ::          </div>
		<script type="text/javascript">
		var gaJsHost = (("https:" == document.location.protocol) ? "https://ssl." : "http://www.");
		document.write(unescape("%3Cscript src='" + gaJsHost + "google-analytics.com/ga.js' type='text/javascript'%3E%3C/script%3E"));
		</script>
		<script type="text/javascript">
		try {
		var pageTracker = _gat._getTracker("UA-7325759-1");
		pageTracker._trackPageview();
		} catch(err) {}</script>
                </body>
                </html><html>
</html>
virgl@PachecosPuter:~$ 

```

---

### Post by KhensuRA on 2010-10-28
**[SIZE="4"]Here is a screen shot, of what happens when I try to update software.[/SIZE]**


[IMG]http://i965.photobucket.com/albums/ae136/hooligans_offroad/Ironhide/Screenshot.jpg[/IMG]

---

### Post by beew on 2010-10-28
> **KhensuRA said:**
> This is what I get when i try using the code you gave me in the terminal.

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

In Maverick whenever you add a ppa, both the software list and the  source code list would be included (checked in Synaptic). Now Medibuntu  has non -free software so of course the source codes are not available.  The program manager is stuck looking for it (You will encounter the same problem if you enable, say, the Opera ppa, because Opera is closed source) 

Just open Synaptic, go to settings > repositories > other  software. Find the line that look like Medibuntu source codes and  uncheck it, then  reload and you should be fine.

---

### Post by beew on 2010-10-28
> **wojox said:**
> Go to System > Administration > Software Sources and get uncheck the Medibuntu repo's and try again.


"System > Admin> Software sources" is no longer in 10.10.

---

### Post by KhensuRA on 2010-10-28
> **beew said:**
> In Maverick whenever you add a ppa, both the software list and the  source code list would be included (checked in Synaptic). Now Medibuntu  has non -free software so of course the source codes are not available.  The program manager is stuck looking for it (You will encounter the same problem if you enable, say, the Opera ppa, because Opera is closed source) 

Just open Synaptic, go to settings > repositories > other  software. Find the line that look like Medibuntu source codes and  uncheck it, then  reload and you should be fine.

Beew, So I tried this and well no luck, still an issue. Here is a another screen shot of what happens when I go to settings > repositories > other  software.. Thanks for all your help thus far.

[IMG]http://i965.photobucket.com/albums/ae136/hooligans_offroad/Ironhide/Screenshot-1.png[/IMG]

---

### Post by beew on 2010-10-28
Ok, just remove the problematic line from the sources list.

In the terminal type

```
gksudo gedit /etc/apt/sources.list.d
```

Find the offending line (medibuntu.list) and delete it. Then save and close the document and in the terminal 

```
 sudo apt-get update 
```

---

### Post by KhensuRA on 2010-10-28
Grrrr!! I get another error when trying this.

/etc/apt/sources.list.d is a directory.
Please check that you typed the location correctly and try again.

Going to owe you some beer after this..

---

### Post by beew on 2010-10-28
Sorry, my bad. Should have known, I was thinking of editing the sources list.

Just get rid of the medibuntu list then'

```
sudo rm /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update
```

---

### Post by KhensuRA on 2010-10-28
Okay so I tried this code.


```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list

```

And a text pad poped up. I can add it here if you like but it is a lot of code.

---

### Post by KhensuRA on 2010-10-28
> **beew said:**
> Sorry, my bad. Should have known, I was thinking of editing the sources list.

Just get rid of the medibuntu list then'

```
sudo rm /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update
```

Oh heck yeah I think that worked!!!! Just need to reboot!!!

---

### Post by KhensuRA on 2010-10-28
Thank you so much!! It worked!!! yay.. 

And I think I will be able to fix it if it ever happens again.

Again thanks for your help..

---

### Post by beew on 2010-10-28
You are very welcome. :)

---

