---
title: "Firefox web error"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by John Hale on 2009-03-15
While trying to access the ford direct website, I keep getting this error message after doing the search any help how to do what it says or how to fix this as I'm not conversant in linux.

Server Error in '/' Application.
Runtime Error
Description: An application error occurred on the server. The current custom error settings for this application prevent the details of the application error from being viewed remotely (for security reasons). It could, however, be viewed by browsers running on the local server machine.

Details: To enable the details of this specific error message to be viewable on remote machines, please create a <customErrors> tag within a "web.config" configuration file located in the root directory of the current web application. This <customErrors> tag should then have its "mode" attribute set to "Off".

<!-- Web.Config Configuration File -->

<configuration>
    <system.web>
        <customErrors mode="Off"/>
    </system.web>
</configuration>


Notes: The current error page you are seeing can be replaced by a custom error page by modifying the "defaultRedirect" attribute of the application's <customErrors> configuration tag to point to a custom error page URL.

<!-- Web.Config Configuration File -->

<configuration>
    <system.web>
        <customErrors mode="RemoteOnly" defaultRedirect="mycustompage.htm"/>
    </system.web>
</configuration>



Thanks

John

---

### Post by peakshysteria on 2009-03-15
Do you mean [http://www.ford.com?](http://www.ford.com?) And could you tell us a bit more about your system and setup. Nothing wrong with the site from my end.

My Firefox Information

Last updated: Sun, 15 Mar 2009 21:45:24 GMT
User Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.7) Gecko/2009030422 Ubuntu/8.10 (intrepid) Firefox/3.0.7

**Extensions** (enabled: 19, disabled: 0; total: 19)
[list]
[*][Autohide](http://www.krickelkrackel.de/autohide/) 1.3.1 
[*][Dictionary Switcher](http://en.design-noir.de/mozilla/dictionary-switcher/) 1.0 
[*][Dictionary Tooltip](http://www.rjonna.com/ext/dictionarytip.php) 1.3 
[*][DownloadHelper](http://www.downloadhelper.net) 4.2 
[*][Flashblock](http://flashblock.mozdev.org/) 1.5.8 
[*][Forecastfox](http://forecastfox.mozdev.org/) 0.9.8 
[*][Greasemonkey](http://www.greasespot.net/) 0.8.20090123.1 
[*][Highlighter](http://hashcolouredtabs.mozdev.org/highlighter/) 0.1.4 
[*][InfoLister](http://mozilla.doslash.org/infolister) 0.10 
[*][last.fmCode](http://mll2.free.fr/?p=42) 0.7b 
[*][Linkification](http://yellow5.us/firefox/linkification/) 1.3.5 
[*][Locationbar²](http://en.design-noir.de/mozilla/locationbar2/) 1.0.3 
[*][Nightly Tester Tools](http://www.oxymoronical.com/web/firefox/nightly) 2.0.2 
[*][Norsk Bokmål og Nynorsk ordliste]() 2.0.10.0 
[*][Tab Mix Plus](http://tmp.garyr.net) 0.3.7.3 
[*][Text Link](http://piro.sakura.ne.jp/xul/_textlink.html.en) 3.0.2009030901 
[*][Tiny Menu](http://trac.arantius.com/wiki/Extensions/TinyMenu) 1.4.9 
[*][Ubuntu Firefox Modifications]() 0.6 
[*][Update Channel Selector](http://www.oxymoronical.com/web/firefox/updatechannel) 1.0.3 
[/list]

**Themes** (7)
[list]
[*]Camifox [selected]
[*]Default 
[*]Dustfox 
[*]Elementary Theme 
[*]Gradient iCool 
[*]myFireFox 
[*]Qute 3++ (custom mod) 
[/list]

**Plugins**
[list]
[*]Default Plugin
[*]Demo Print Plugin for unix/linux
[*]DivX® Web Player
[*]Java(TM) Plug-in 1.6.0_10-b33
[*]QuickTime Plug-in 7.2.0
[*]Shockwave Flash
[*]Totem Web Browser Plugin 2.24.3
[*]Windows Media Player Plug-in 10 (compatible; Totem)
[/list]

---

### Post by John Hale on 2009-03-15
The site loads fine, I go into the second hand ford direct bit then into the search engine for cars and all this loads fine, then when I press the locate button I get the above problem. I don't how to list the info you've shown sorry

---

### Post by chrisod on 2009-03-15
I just went to [http://forddirect.com](http://forddirect.com), clicked on a model, then clicked on the search feature and it all worked fine. Without knowing what version of Ubuntu and Firefox you have, and what extensions you have installed, there isn't much we can do to help. Do you have any ad or script blocker add-ons running? They could be screwing with the flash on the site. Turn then off and try again.

---

### Post by chrisod on 2009-03-15
OK, I just noticed your UK location. Is it possible that the Ford site is US only, and what you are seeing is a very badly formatted error message?

---

### Post by John Hale on 2009-03-16
The website isn't US only as 18 months ago under windows my mum got a car reserved via it that she later used, my ubuntu is hardy heron 8.04 anf Firefox is version 3.0.7.

---

### Post by orethrius on 2009-03-16
> **John Hale said:**
> The website isn't US only as 18 months ago under windows my mum got a car reserved via it that she later used, my ubuntu is hardy heron 8.04 anf Firefox is version 3.0.7.
Was she using Internet Explorer by any chance?  This could be one of those fabled "IE-only" sites that went the way of the dodo once Firefox caught on over here.

---

