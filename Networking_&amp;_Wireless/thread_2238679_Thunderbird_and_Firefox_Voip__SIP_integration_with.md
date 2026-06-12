---
title: "Thunderbird and Firefox Voip / SIP integration with Linphone and Telify or TBDialOut"
date: 2014-08-09
forum: Networking &amp; Wireless
---

### Post by eni2 on 2014-08-09
Hello everyone,

I'm doing this little post because I had really hard time doing this.

So here's what I wanted to do : 

I wanted to make to have the phone numbers in my Thunderbird Contacts to  be cliclable and start automatically Linphone to call over a Voip  provider. I used [www.freevoipdeal.com]("http://www.freevoipdeal.com") SIP provider, which is the cheapest for my country.

Here's what you have to do:


[LIST=1]
[*]Go grab [TBDialOut]("https://addons.mozilla.org/en-us/thunderbird/addon/tbdialout/") or [Telify]("https://addons.mozilla.org/de/thunderbird/addon/telify/") extension for thunderbird ([firefox]("https://addons.mozilla.org/de/firefox/addon/telify/")) and install it 
[*]Install Linphone and configure your Voip PC-to-Phone account. Make sure it is default. 
[*]In  your contacts, make sure to have the right format for the phone  numbers. Don't put any "-" or spaces. You normally need to add the  country prefix (1 for US and Canada). So a phone number in Canada would  look like : 18197895632 (country code, area code, phone number) 
[*]After that, you need to ensure that SIP url are handled throught xdg-open : 
[*]Open your /home/{user}/.local/share/applications/mimeapps.list file 
[*]Add this line      
     ```
x-scheme-handler/sip=linphone-call.desktop
``` 
[*]Open Thunar or Nautilus in root mode (For Ubuntu write in Terminal: gksudo nautilus) 
[*]Go to /usr/share/applications 
[*]Copy linphone.desktop in the same folder and rename it linphone-call.desktop 
[*]Again, in root mode, open the linphone-call.desktop file (For Ubuntu write in Terminal, then browse to file: sudo gedit) 
[*]Add that line at the end of the file      
     ```
MimeType=x-scheme-handler/sip
``` 
[*]Go to the Exec line and replace it with      

     ```
Exec=linphone -c %U
``` 
[*]Last, you must configure TBDialOut/Telify Extension : 
[*]Go to the preferences dialog of the extension 
[*]Choose custom URL 
[*]Enter the following (changing it if you have another provider than diamondcard) 
     ```
sip:$0@sip.freevoipdeal.com 
``` 
[/LIST]


You are good to go!

For reference here are Jonathans sources of Info:
[http://superuser.com/questions/16209...tocol-with-xdg]("http://superuser.com/questions/162092/how-can-i-register-a-custom-protocol-with-xdg")
[http://www.oak-wood.co.uk/faq/conten...-_-ubuntu.html]("http://www.oak-wood.co.uk/faq/content/5/14/en/how-do-i-register-a-url-handler-for-the-sip-protocol-in-gnome-_-ubuntu.html")
[http://www.oak-wood.co.uk/faq/conten...ith-ekiga.html]("http://www.oak-wood.co.uk/faq/content/3/19/en/how-do-i-use-tbdialout-with-ekiga.html")
[https://www.oak-wood.co.uk/faq/conte...y-running.html]("https://www.oak-wood.co.uk/faq/content/4/17/en/i_m-using-ekiga-for-sip-connections-but-when-i-dial-i-get-the-error-ekiga-is-already-running.html")

special thx to [Jonathan and his post for Ekiga]("http://ubuntuforums.org/showthread.php?t=2123659") (I hope you apologize for just copying and editing your post, I've been too lazy to write the whole thing again)

Eni2

---

