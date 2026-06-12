---
title: "Problem connecting to alislam.org.  No, the site isn't down!  HTTP/Network issue??"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by mirzmaster on 2007-09-14
Hello, all.  I had originally posted this problem in General Help where it didn't seem to get much attention (perhaps due to the speed at which posts are pushed off the front page there :) ).  For reference, the earlier thread is:  [http://ubuntuforums.org/showthread.php?t=549758](http://ubuntuforums.org/showthread.php?t=549758)

This newer thread has a bit more detail.

So, the problem is that I'm having trouble accessing one particular website on the web, [http://www.alislam.org/](http://www.alislam.org/).  The problem in accessing it is a particularly strange one.  Where the site fails to load, it seems only part of the HTML content is being downloaded and then the page load stalls.  The throbber in Firefox continues throbbing, but the site will not finish loading.

I should add that I first encountered problems in trying to load the site only a few weeks ago (I don't recall exactly when).  I don't recall the problem coinciding with a particular update or anything.

Here is the behaviour I am seeing across various platforms and browsers:

[LIST]
[*]Feisty, Firefox 2.0.0.6 **(my default setup)** -- [COLOR="Red"]Site fails to load in its entirely.[/COLOR]
[*]Feisty, Firefox 2.0.0.5 -- [COLOR="Red"]Site fails to load in its entirety.[/COLOR]
[*]Feisty, Firefox 1.5.0.12 -- [COLOR="Red"]Site fails to load in its entirety.[/COLOR]
[*]Feisty, Firefox 3.0a8pre -- [COLOR="Red"]Site fails to load in its entirety.[/COLOR]
[*]Feisty, Seamonkey 1.1.3 -- [COLOR="Red"]Site fails to load in its entirety.[/COLOR]
[*]Feisty, Galeon 2.0.2 -- [COLOR="Red"]Site fails to load in its entirety.[/COLOR]
[*]Feisty, Opera 9.23 -- [COLOR="Red"]Site fails to load in its entirety.[/COLOR]
[*]Feisty, Lynx 2.8.5rel.1 -- [COLOR="Red"]Site fails to load in its entirety[/COLOR] (despite the face that Lynx shows HTTP 1.1/200).
[*]Dapper, Firefox 1.5.0.? -- [COLOR="Green"]Loads successfully![/COLOR]
[*]Feisty, Windows XP VMWare Guest, Firefox 2.0.0.6 -- [COLOR="Green"]Loads successfully![/COLOR]
[*]Windows XP, Firefox 2.0.0.6 -- [COLOR="Green"]Loads successfully![/COLOR]
[*]All Platforms, Proxify.com -- [COLOR="Green"]Loads successfully![/COLOR]  ([http://proxify.com/p/000010A1000100/687474703a2f2f616c69736c616d2e6f72672f](http://proxify.com/p/000010A1000100/687474703a2f2f616c69736c616d2e6f72672f))
[/LIST]

Now, from the above, the problem appears to be isolated to browsers running natively in Feisty.  I've had another friend verify that he too is experiencing the problem.  He is running Feisty as well.

Can anyone verify that they are experiencing the same problem, or speculate on why this problem may be occurring?

By the way, this may be of interest... the partial HTML source of the site that does manage to come down.  You can see that it is clearly incomplete, and thus nothing actually renders:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"><html xmlns="http://www.w3.org/1999/xhtml">






<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
<title>Al Islam Online - Ahmadiyya Muslim Community</title>
<meta name="Description" content="Al Islam - Official website of Ahmadiyya Muslim Community - a religious organization, international in its scope, with branches in over 189 countries.  This is the most dynamic denomination of Islam in modern history, with worldwide membership exceeding tens of millions." />
<meta name="Keywords" content="ahmadiyya, ahmadiyya movement, worldwide ahmadiyya movement,ahmadiyya movement in islam, islam ahmadiyyat , ahmadiyyat, ahmadi, mirza masroor ahmad, islamic organization, sects in islam , khilafat, prophet muhammad" />
<Meta http-equiv="expires" content="Never">
<Meta name="robots" content="All">
<META name="revisit-after" content="7 Days">
<Meta name="distribution" content="Global”>
<Meta name="classification" content="Religion">

<link rel="search" href="opensearchdescription.xml" type="application/opensearchdescription+xml" title="alislam.org" />

<link href="sitewide-styles/homepage-styles.css" rel="stylesheet" type="text/css" />
<link href="dynamic-homepage-content/jalsa/jalsa.css" rel="stylesheet" type="text/css" />



<link href="dynamic-homepage-content/primary/active/ramadhan/primary.css" rel="stylesheet" type="text/css" />
<script language="javascript" src="sitewide-scripts/scroll/ts_files/scroll.js"></script>
<script src="sitewide-scripts/jumpmenu.js" language="javascript" type="text/javascript"></script>

</head>

<body id="page-body" leftmargin="0" topmargin="0" marginwidth="0" marginheight="0">

<div id="youtube-layer" style="background: #000000; position:absolute; top:0; left:0; right:0; bottom:0; z-index:10002; filter: alpha(opacity=60); -moz-opacity: 0.6; opacity:0.6; height:100%; width:100%; display: none;"></div>
<div id="youtube-promo" style="position: fixed; background: #ffffff; left: 40%; top: 50%;  margin-top: -50px; margin-left: -100px;  z-index:999999; display: none;">
 <table cellspacing="0" cellpadding="4">
 <tr bacground="green"><td background="green" align="right" v-align="middle">

 <a href="javascript:closeyoutube();"><font-face="areal">close</font></a>&nbsp;</td></tr>
 <tr><td>
</td>
</tr></table>
 </div>

<div id="overDiv" style="position:absolute; visibility:hidden; z-index:1000;"></div>
<div id="container-page">
  <div id="container-branding" class="clearfix">
    <div id="container-bismillah">
      <p id="bismillah" class="replace" title="In the Name of Allah, The Most Gracious, Ever Merciful"><span class="empty"></span><em><span class="accessible">In the Name of Allah, The Most Gracious, Ever Merciful.</span></em></p>
    </div>
    <div id="container-logo">
      <h1 id="logo" class="replace" title="Al Islam - The official website of the Ahmadiyya Muslim Community"><span class="empty"></span><span class="accessible">Al Islam</span></h1>

    </div>
    <div id="container-tagline">
      <p id="tagline" class="replace" title="Love for All, Hatred for None"><span class="empty"></span><span class="accessible">Love for All, Hatred for None.</span></p>
    </div>
  </div>
  <div id="container-body" class="clearfix">
    <div id="container-sidebar" class="clearfix">
        <!-- Site Search -->

      <div id="site-search">
		<FORM method=GET action=http://www.google.com/u/alislam>
           <h2><label for="sitesearch">Search Al Islam</label></h2>
           <input name="q" type="text" id="sitesearch" size="16" maxlength="255" />
           <button id="sitesearch-button" name="sa" type="submit">Search</button>
        </form>
      </div>

	<!-- Site Search End -->
      <!-- Site Navigation -->
      <div id="container-nav">
        <h2 class="accessible">Browse Al Islam</h2>
        <ul id="nav-main">
          <li id="active"><span id="current">Home</span></li>
          <li><a href="/library/islam.html">Islam</a></li>

          <li><a href="/introduction/index.html">Ahmadiyyat</a></li>
          <li><a href="/library/">Library</a></li>
          <li><a href="http://store.alislam.org/" target="_blank">Online Store</a></li>
        </ul>
      </div>
      <!-- Language -->


			<div id="nav-language"><form action="language.php" method="POST">

          <h2>Language:</h2>
          <ul class="clearfix">
            <li id="button-urdu" title="Urdu"><a href="/urdu/">Urdu</a></li>
            <li id="button-arabic" title="Arabic"><a href="http://www.islamahmadiyya.net/" target="_blank">Arabic</a></li>
          </ul>
          <select name="language" onchange="MM_jumpMenu('parent',this,0)">

            <option selected="selected">- Other -</option>
            <option value="/chinese/Chinese.htm">Chinese</option>
            <option value="/spanish/">Español</option>
            <option value="/french/">Français</option>
			<option value="/japan/">Japanese</option>
            <option value="/malayalam/">Malayalam</option>

            <option value="/russian/">Russian</option>
            <option value="/swahili/">Swahili</option>
            <option value="/turkish/">T&uuml;rk&ccedil;e</option>
			<option value="/affiliated-websites.php">-- Countries --</option>
          </select>
          
```

In addition to the above details which are taken from the original thread in General Help, I can offer further details.

I've even tried to wget the URL to see what would happen:

```
--02:44:37--  http://www.alislam.org/
           => `index.html'
Resolving www.alislam.org... 66.250.64.42
Connecting to www.alislam.org|66.250.64.42|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [            <=>                                                                                   ] 5,496         --.--K/s             
```

After getting the first 5,496 bytes, nothing else happens.

I've also run a traceroute to the site but that seems route just fine.  I've compared it to the windows traceroute and I can't see any significant differences.

Does anyone know what might be causing this issue?  It appears to be a low-level networking or HTTP issue, but this is just my uneducated guess.  I tried to use Wireshark to look for anything that stood out as a problem, but I wasn't very successful.  I'm afraid I don't have the know-how for HTTP and network analysis.

**Again, from what I can tell this site loads perfectly outside of Feisty, and via anonymous proxy.  I am experiencing no issues with any other sites.**

Any clues?  :confused:  Any idea what I can try next?  If someone can help look into this issue, I'd be perfectly willing to aid in any way I can.

---

### Post by rivalarrival on 2007-09-14
Feisty, Firefox 2.0.0.6 - loaded fine

Those browsers don't all use the same cache, do they?

---

### Post by mirzmaster on 2007-09-14
> **rivalarrival said:**
> Feisty, Firefox 2.0.0.6 - loaded fine

Those browsers don't all use the same cache, do they?

Nope.  They are all using different profiles.

By the way I know of at least two other people who are having problems loading the site.  One is a friend also running Feisty, Firefox 2.0.0.6, and another was a poster in the first thread I started in General Help.  So you're the first person to report that it loaded fine.

This leads me to believe that perhaps it has to do with a particular package I may have installed?

**Any idea what I should be looking for?**

And, because it may come up, my iptables are empty:

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

---

### Post by mirzmaster on 2007-09-15
*bump*

---

