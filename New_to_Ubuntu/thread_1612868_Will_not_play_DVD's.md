---
title: "Will not play DVD's"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by muddpup64 on 2010-11-03
My movie player will not play Toy Story 3. It brings up the language selection, but when I choose the movie stops and says;```
 An Error Occurred: Could not read from resource 
```Help.

---

### Post by ArgusVision on 2010-11-03
Are you using 10.10? What player are using? Do have the media codecs installed? This may sound like a dumb question, but I have to ask. Are you certain it is a DVD and not Blueray. I only ask that because I've seen that happen before.

---

### Post by coffeecat on 2010-11-03
Do you have libdvdcss2 installed? You need that for commercial encrypted DVDs. If you don't, someone else can help you because I'm going to bed. :)

---

### Post by ArgusVision on 2010-11-03
Coincidentally, a friend of mine just rented that movie.So I thought I'd try it out. I got the same error. I'm running 10.04 with the libdvdcss2 codec,(all the codecs fromm medibuntu). I tried it on "Movie Player" and received the same error. I tried VLC, and it showed the menu, then went back to the controls, no video, no error out. 
To attempt to see the error output I ran it from terminal and got the following.

me@mypc:~$ vlc /dev/sr0
VLC media player 1.0.6 Goldeneye
[0x875d668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
[COLOR="Red"]libdvdread: Encrypted DVD support unavailable.[/COLOR]
************************************************
**                                            **
**  [COLOR="Red"]No css library available.[/COLOR] See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: TOY_STORY_3_RENTAL
libdvdnav: DVD Serial Number: 3D129947
libdvdnav: DVD Title (Alternative): TOY_STORY_3_RENTAL
[COLOR="Red"]libdvdnav: Unable to find map file '/home/me:)/.dvdnav/TOY_STORY_3_RENTAL.map'[/COLOR]
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
[COLOR="Red"][0x8811700] main input error: ES_OUT_RESET_PCR called
[0x8811700] main input error: ES_OUT_RESET_PCR called[/COLOR]
[0x8b3b470] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0xb7120720] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0xb7120720] pulse audio output: No. of Audio Channels: 2
[0x8811700] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 300 ms
[0x8811700] main input error: ES_OUT_RESET_PCR called
[0xb7120720] pulse audio output: No. of Audio Channels: 2
[0x8811700] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 1879 ms
[0x8811700] main input error: ES_OUT_RESET_PCR called
[0x8811700] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 1909 ms
[0x8811700] main input error: ES_OUT_RESET_PCR called
[0x8811700] main input error: ES_OUT_RESET_PCR called
[0x8811700] main input error: ES_OUT_RESET_PCR called
[0x8811700] main input error: ES_OUT_RESET_PCR called


Sorry that doesn't do much more than confirm your issue.

[COLOR="Blue"]EDIT: Well I thought I had libdvdcss2 installed... (see first red line) Going to attempt to re-install from medibuntu. [/COLOR]

---

### Post by muddpup64 on 2010-11-03
Yes 10.10. Movie Player and/or Moovida Media Center. What are media codecs? Yes it is a DVD.And I do not have  libdvdcss2 installed.

---

### Post by waynefoutz on 2010-11-03
> **muddpup64 said:**
> Yes 10.10. Movie Player and/or Moovida Media Center. What are media codecs? Yes it is a DVD.And I do not have  libdvdcss2 installed.

well, you need to install it through synaptic. that, and libdvdread4 I would install ubuntu-restricted-extras as well.

---

### Post by waynefoutz on 2010-11-03
double post....

---

### Post by Sylslay on 2010-11-03
I play after that,

sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh 

Goodnight

1st play dvd on Ubuntu last Tue :-),

---

### Post by ArgusVision on 2010-11-03
:oops:
OK. So I checked my repos and saw that I did enable medibuntu, but apparently did not install libdvdcss2. (Just recently reinstalled and must have forgotten.) Installed libdvdcss2 and dvds are working fine.

Try Sylslay's suggestion first if that doesn't do it for you go to the medibuntu repos how to and follow the instructions. 

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository)

---

### Post by muddpup64 on 2010-11-03
Synaptic says libdvdcss2 does not exsist.

---

### Post by arju305 on 2010-11-03
> **Sylslay said:**
> I play after that,

sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh 

Goodnight

1st play dvd on Ubuntu last Tue :-),


sorry to break the thread ..... but i could not stop asking........
sudo /usr/share/doc/libdvdread4/install-css.sh 
what does this command do.???

---

### Post by Zzl1xndd on 2010-11-03
If you already have the Restricted extras installed just open a terminal and enter 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

This will add the Ability to read encrypted DVD's. 

Alternatively you could by the Fluendo DVD player from the Software centre. However I would recommend using the Script :)

---

### Post by muddpup64 on 2010-11-03
> If you already have the Restricted extras installed just open a terminal and enter 

 	Code:
 	sudo /usr/share/doc/libdvdread4/install-css.sh 
This will add the Ability to read encrypted DVD's. 

Alternatively you could by the Fluendo DVD player from the Software centre. However I would recommend using the Script :smile: 

Still nothing.

---

### Post by muddpup64 on 2010-11-04
Sorry but you going to give me a play by play. I know it's a pain, and I'm sorry if I'm being irritating. But it just won't work. Sometimes it takes me a while to understand. I thank you for your   patience.

---

### Post by wojox on 2010-11-04
> **muddpup64 said:**
> Still nothing.

```
sudo apt-get install libdvdread4
```

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

Reboot. :)

---

### Post by trikster_x on 2010-11-04
Open a terminal and paste in the following commands.

First thing, add the medibuntu repository.  This is what has all the package info you will need for a great many multimedia programs and libs:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Next, add the package-list to software center and enable bug report filing against the packages:
```
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```

Finally we install libdvdcss2 (for newer dvd playback) and restricted extras (for older dvd's and any audio and video codecs you might need):
```
sudo apt-get install libdvdcss2 ubuntu-restricted-extras
```

Now you should have full playback capabilities.

---

### Post by muddpup64 on 2010-11-04
Thank You! You Rock! :guitar:


My horrible day just turned great.

---

### Post by ArgusVision on 2010-11-04
Great! be sure to mark the thread solved.

---

### Post by theozzlives on 2010-11-04
well, I don't play DVDs on my computer. I tried the instructions nontheless. I can't play Click which is no biggie, but it means something ain't working right.

---

### Post by zoftware on 2010-11-04
OK... Using a Sony VAIO VGC-LS20E 

It keeps failing with Windows Vista sooo...

I installed Ubuntu 10.4.

I performed all updates, twice... and the ran the driver updates for good measure with a restart.

So now I have SIX DVDs (legal from different companies).

When I insert any of them, I am prompted to choose an application. I chose Movie Player.

Then all give the same message:

"An error occurred"
"Could not read from resource."

So I quoted the error message and searched Google, the Ubuntu forums, and Sony's website (ZERO).

Yes, I read this entire thread.

I used the Synaptic Package Manager and installed ubuntu-restricted-extras and the VLC stuff.

Restarted again... same results... same messages.

So I started from scratch, reformatted the hard drive again, and installed Ubuntu 10.10.

Repeated the entire process... same results... same messages.

:confused:

PS This system is used primarily by my neighbors 6 and 4 year-old girls. I am trying to be a good samaritan.

---

### Post by muddpup64 on 2010-11-04
I'm afraid we have a problem, recently after installing the files for playing dvds, I now can not get into synaptic and/or update manager.
 Telling me: ```
E: Type '<!DOCTYPE' is not known on line 3 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```I think it might have something to do with the new installed programs.
What should I do?

---

### Post by zoftware on 2010-11-05
Well [Sylslay]("http://guide.ubuntuforums.org/member.php?u=739078") gave us the answer:

sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh 

But I could not connect the dots until [tweakedenigma]("http://guide.ubuntuforums.org/member.php?u=161141") let us know that these instructions should be inserted into the terminal.

Bingo! I can deliver this computer to the girls tomorrow...
and it will play DVD movies for them.

Thanks everybody.

:P

---

### Post by coffeecat on 2010-11-05
> **muddpup64 said:**
> I'm afraid we have a problem```
E: Type '<!DOCTYPE' is not known on line 3 in source list /etc/apt/sources.list.d/medibuntu.list

```I think it might have something to do with the new installed programs.
What should I do?

It has to do with the .list file for Medibuntu. Somehow, there is a malformed line. It's easy to fix, but first we need to see the contents of the file.

Open a Nautilus file browser and navigate to /etc/apt/sources.list.d/. That's the folder called 'sources.list.d' in the apt folder, not the file 'sources.list'. In the 'sources.list.d' folder there is a file called 'medibuntu.list'. Open it by right-clicking on it and 'open with' gedit/text-editor. **Do not** double-click on it.

You will now see the contents read-only. Copy and paste them into your next post (in code tags) and someone will be able to tell you how to edit out the error.

---

### Post by muddpup64 on 2010-11-05
Here is the file you asked for:
```
 <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"> 
<html> 
<head> 
<title>HughesNet Customer Care - Payment Redirect</title> 
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"> 
<link href="style/style.css" rel="stylesheet" type="text/css"> 
<script language="JavaScript"> 
<!-- 
 
 
 
 
function openNewWindow(URLtoOpen, windowName, windowFeatures) { 
newWindow=window.open(URLtoOpen, windowName, windowFeatures); } 
//--> 
</script> 
<style type="text/css"> 
<!-- 
.style1 {color: #FF0000} 
--> 
</style> 
</head> 
<body bgcolor="#FFFFFF" leftmargin="0" topmargin="0" marginwidth="0" marginheight="0"> 
<table width="700" border="0" align="center" cellpadding="0" cellspacing="0"> 
  <tr>  
    <td><table width="100%" border="0" cellspacing="0" cellpadding="0"> 
 
        <tr>  
          <td align="left"><img src="images/header-left-hn.gif" width="459" height="98"></td> 
          <td width="55%" background="images/headerbg-hn.gif">&nbsp;</td> 
          <td align="right"><img src="images/header-rite-hn.gif" width="206" height="98"></td> 
        </tr> 
      </table></td> 
  </tr> 
</table> 
<table width="700" border="0" align="center" cellpadding="0" cellspacing="0"> 
  <tr> 
    <td width="14" background="images/left-column-bg2.gif">&nbsp;</td> 
    <td bgcolor="#FFFFFF"><table width="100%" border="0" align="center" cellpadding="7" cellspacing="0"> 
        <tr>  
          <td width="100%" align="left" valign="top" class="mainText"><table width="100%" border="0" cellpadding="0" cellspacing="0" bordercolor="#FFFFFF"> 
              <tr>  
                <td width="10%" valign="top" class="bodytext">&nbsp;</td> 
                <td width="81%" valign="top" class="mainText"><p class="mainText">&nbsp;</p> 
                  <p><b>This message is being sent to you directly from HUGHES.  To continue using your HughesNet<font size="-1"><sup>&reg;</sup></font> service, it is important that you take immediate payment action.</b></p> 
                  <p><b>We were unable to process your monthly payment using the credit or debit card information that we have on file for your account. Please follow the instructions below to update your credit/debit card information and pay your bill.</b></p> 
                   
                   
                  <ul><li>Make a one-time payment without logging in by clicking the “Pay Without Logging In” button below.  All you need is your <a href="http://customer.kb.hughesnet.com/Pages/1043.aspx">Site 
                      Account Number</a> and your billing zip code.</li></ul> 
                       
                  <table width="80%" border="0" align="center" cellpadding="3" cellspacing="0" class="mainText"> 
   
  <tr> 
    <td align="center" valign="top"><a href="https://www.myhughesnet.com/amserver/UI/Login?IDToken1=mkpuser1&IDToken2=mkpuser1&goto=https://www.myhughesnet.com/bws/csr/csr_search_new.jsp" target="_blank"><img src="images/pay_without_on.gif" alt="Pay without logging in" width="200" height="43" border="0"></a></td> 
    </tr> 
                  </table> 
    <p>Alternately, you can go to <a href="http://www.customercare.myhughesnet.com/">www.customercare.myhughesnet.com</a>.</p>             
                 
        <ul> 
          <li>Access your account information by selecting the “Login” option under the “Account Information” section and then selecting “Billing.”  From there, you can update your credit/debit card information for immediate payment as well as check your account balance, and view your invoices and payment history.</li> 
        </ul>       
  
  <p><b>Please make your payment today to prevent your account from being 
      suspended or closed.</b> Web page redirects to this site will continue 
      until your account has been paid or closed and will end approximately four 
      hours after payment has been made.</p> 
  <p>*******<br> 
    If your account is suspended, <b>your service will be interrupted until you 
    clear any outstanding balance</b>. Once you have settled your account, you 
    will be given instructions on how to reactivate your account.</p> 
  <p>If your account is closed, you may also be subject to early termination 
    fees and other fees pursuant to the terms of your Subscriber Agreement.</p> 
  <p>Thank you for your prompt attention to this matter.<br> 
    <br> 
  </p></td> 
  <td width="10%" valign="top" class="bodytext">&nbsp;</td> 
              </tr> 
            </table> </td> 
        </tr> 
    </table></td> 
    <td width="12" background="images/rite-column-bg2.gif">&nbsp;</td> 
  </tr> 
</table> 
 
<table width="700" border="0" align="center" cellpadding="0" cellspacing="0"> 
  <tr>  
    <td width="48"><img src="images/footer-left.gif" width="48" height="44"></td> 
        <td width="610" align="center" background="images/footer-bg.gif" class="footerWhite"><a href="javascript:openNewWindow('http://www.hughes.com','legal','resizable=yes,top=190,left=120,height=700,width=832,alwaysRaised=yes,dependent=yes,status=no,toolbar=no,scrollbars=yes')" class="footerWhite">&copy;2010  
      HUGHES</a> | <a href="javascript:openNewWindow('about.html','legal','resizable=yes,top=190,left=120,height=700,width=832,alwaysRaised=yes,dependent=yes,status=no,toolbar=no,scrollbars=yes')" class="footerWhite"> About  
      this site</a> | <a href="javascript:openNewWindow('http://www.hughes.com/hughes/Rooms/DisplayPages/LayoutInitial?pageid=privacy','legal','resizable=yes,top=190,left=120,height=700,width=832,alwaysRaised=yes,dependent=yes,status=no,toolbar=no,scrollbars=yes')" class="footerWhite">Privacy  
      Policy</a> | <a href="javascript:openNewWindow('http://www.hughes.com/hughes/Rooms/DisplayPages/LayoutInitial?pageid=fairaccess','legal','resizable=yes,top=190,left=120,height=700,width=832,alwaysRaised=yes,dependent=yes,status=no,toolbar=no,scrollbars=yes')" class="footerWhite">Fair  
      Access Policy</a> | <a href="javascript:openNewWindow('http://www.hughes.com/hughes/Rooms/DisplayPages/LayoutInitial?pageid=subscriber','legal','resizable=yes,top=190,left=120,height=700,width=832,alwaysRaised=yes,dependent=yes,status=no,toolbar=no,scrollbars=yes')" class="footerWhite">Subscriber Agreement</a></td> 
        <td width="42" align="right"><img src="images/footer-rite.gif" width="42" height="44"></td> 
  </tr> 
</table> 
<!-- START OF SDC Advanced Tracking Code --> 
<!-- Copyright (c) 1996-2005 WebTrends Inc.  All rights reserved. --> 
<!-- $DateTime: 2006/03/08 11:31:03 $ --> 
<SCRIPT TYPE="text/javascript"><!-- 
var gService = false; 
var gTimeZone = -5; 
// Code section for Enable First-Party Cookie Tracking 
function dcsCookie(){ 
    if (typeof(dcsOther)=="function"){ 
        dcsOther(); 
    } 
    else if (typeof(dcsPlugin)=="function"){ 
        dcsPlugin(); 
    } 
    else if (typeof(dcsFPC)=="function"){ 
        dcsFPC(gTimeZone); 
    } 
} 
function dcsGetCookie(name){ 
    var pos=document.cookie.indexOf(name+"="); 
    if (pos!=-1){ 
        var start=pos+name.length+1; 
        var end=document.cookie.indexOf(";",start); 
        if (end==-1){ 
            end=document.cookie.length; 
        } 
        return unescape(document.cookie.substring(start,end)); 
    } 
    return null; 
} 
function dcsGetCrumb(name,crumb){ 
    var aCookie=dcsGetCookie(name).split(":"); 
    for (var i=0;i<aCookie.length;i++){ 
        var aCrumb=aCookie[i].split("="); 
        if (crumb==aCrumb[0]){ 
            return aCrumb[1]; 
        } 
    } 
    return null; 
} 
function dcsGetIdCrumb(name,crumb){ 
    var cookie=dcsGetCookie(name); 
    var id=cookie.substring(0,cookie.indexOf(":lv=")); 
    var aCrumb=id.split("="); 
    for (var i=0;i<aCrumb.length;i++){ 
        if (crumb==aCrumb[0]){ 
            return aCrumb[1]; 
        } 
    } 
    return null; 
} 
function dcsFPC(offset){ 
    if (typeof(offset)=="undefined"){ 
        return; 
    } 
    if (document.cookie.indexOf("WTLOPTOUT=")!=-1){ 
        return; 
    } 
    var name=gFpc; 
    var dCur=new Date(); 
    var adj=(dCur.getTimezoneOffset()*60000)+(offset*3600000); 
    dCur.setTime(dCur.getTime()+adj); 
    var dExp=new Date(dCur.getTime()+315360000000); 
    var dSes=new Date(dCur.getTime()); 
    WT.co_f=WT.vt_sid=WT.vt_f=WT.vt_f_a=WT.vt_f_s=WT.vt_f_d=WT.vt_f_tlh=WT.vt_f_tlv=""; 
    if (document.cookie.indexOf(name+"=")==-1){ 
        if ((typeof(gWtId)!="undefined")&&(gWtId!="")){ 
            WT.co_f=gWtId; 
        } 
        else if ((typeof(gTempWtId)!="undefined")&&(gTempWtId!="")){ 
            WT.co_f=gTempWtId; 
            WT.vt_f="1"; 
        } 
        else{ 
            WT.co_f="2"; 
            var cur=dCur.getTime().toString(); 
            for (var i=2;i<=(32-cur.length);i++){ 
                WT.co_f+=Math.floor(Math.random()*16.0).toString(16); 
            } 
            WT.co_f+=cur; 
            WT.vt_f="1"; 
        } 
        if (typeof(gWtAccountRollup)=="undefined"){ 
            WT.vt_f_a="1"; 
        } 
        WT.vt_f_s=WT.vt_f_d="1"; 
        WT.vt_f_tlh=WT.vt_f_tlv="0"; 
    } 
    else{ 
        var id=dcsGetIdCrumb(name,"id"); 
        var lv=parseInt(dcsGetCrumb(name,"lv")); 
        var ss=parseInt(dcsGetCrumb(name,"ss")); 
        if ((id==null)||(id=="null")||isNaN(lv)||isNaN(ss)){ 
            return; 
        } 
        WT.co_f=id; 
        var dLst=new Date(lv); 
        WT.vt_f_tlh=Math.floor((dLst.getTime()-adj)/1000); 
        dSes.setTime(ss); 
        if ((dCur.getTime()>(dLst.getTime()+1800000))||(dCur.getTime()>(dSes.getTime()+28800000))){ 
            WT.vt_f_tlv=Math.floor((dSes.getTime()-adj)/1000); 
            dSes.setTime(dCur.getTime()); 
            WT.vt_f_s="1"; 
        } 
        if ((dCur.getDay()!=dLst.getDay())||(dCur.getMonth()!=dLst.getMonth())||(dCur.getYear()!=dLst.getYear())){ 
            WT.vt_f_d="1"; 
        } 
    } 
    WT.co_f=escape(WT.co_f); 
    WT.vt_sid=WT.co_f+"."+(dSes.getTime()-adj); 
    var expiry="; expires="+dExp.toGMTString(); 
    document.cookie=name+"="+"id="+WT.co_f+":lv="+dCur.getTime().toString()+":ss="+dSes.getTime().toString()+expiry+"; path=/"+(((typeof(gFpcDom)!="undefined")&&(gFpcDom!=""))?("; domain="+gFpcDom):("")); 
    if (document.cookie.indexOf(name+"=")==-1){ 
        WT.co_f=WT.vt_sid=WT.vt_f_s=WT.vt_f_d=WT.vt_f_tlh=WT.vt_f_tlv=""; 
        WT.vt_f=WT.vt_f_a="2"; 
    } 
} 
 
// Code section for Use the new first-party cookie generated with this tag. 
var gFpc="WT_FPC"; 
var gConvert=true; 
 
function dcsAdv(){ 
    dcsFunc("dcsET"); 
    dcsFunc("dcsCookie"); 
    dcsFunc("dcsAdSearch"); 
    dcsFunc("dcsTP"); 
} 
 
//--> 
</SCRIPT> 
<!-- END OF SDC Advanced Tracking Code --> 
 
<!-- START OF SmartSource Data Collector TAG --> 
<!-- Copyright (c) 1996-2005 WebTrends Inc.  All rights reserved. --> 
<!-- $DateTime: 2006/03/09 14:15:22 $ --> 
<SCRIPT TYPE="text/javascript"><!-- 
var gDomain="sdc.hns.com"; 
var gDcsId="dcsu659jtu379xril69y0rr8e_4z5q"; 
 
if ((typeof(gConvert)!="undefined")&&gConvert&&(document.cookie.indexOf(gFpc+"=")==-1)&&(document.cookie.indexOf("WTLOPTOUT=")==-1)){ 
    document.write("<SCR"+"IPT TYPE='text/javascript' SRC='"+"http"+(window.location.protocol.indexOf('https:')==0?'s':'')+"://"+gDomain+"/"+gDcsId+"/wtid.js"+"'><\/SCR"+"IPT>"); 
} 
//--> 
</SCRIPT> 
<SCRIPT TYPE="text/javascript"><!-- 
var gImages=new Array; 
var gIndex=0; 
var DCS=new Object(); 
var WT=new Object(); 
var DCSext=new Object(); 
var gQP=new Array(); 
var gI18n=false; 
if (window.RegExp){ 
    var RE={"%09":/\t/g,"%20":/ /g,"%23":/\#/g,"%26":/\&/g,"%2B":/\+/g,"%3F":/\?/g,"%5C":/\\/g,"%22":/\"/g,"%7F":/\x7F/g,"%A0":/\xA0/g}; 
    var I18NRE={"%25":/\%/g}; 
} 
 
// Add customizations here 
 
function dcsVar(){ 
    var dCurrent=new Date(); 
    WT.tz=dCurrent.getTimezoneOffset()/60*-1; 
    if (WT.tz==0){ 
        WT.tz="0"; 
    } 
    WT.bh=dCurrent.getHours(); 
    WT.ul=navigator.appName=="Netscape"?navigator.language:navigator.userLanguage; 
    if (typeof(screen)=="object"){ 
        WT.cd=navigator.appName=="Netscape"?screen.pixelDepth:screen.colorDepth; 
        WT.sr=screen.width+"x"+screen.height; 
    } 
    if (typeof(navigator.javaEnabled())=="boolean"){ 
        WT.jo=navigator.javaEnabled()?"Yes":"No"; 
    } 
    if (document.title){ 
        WT.ti=gI18n?dcsEscape(dcsEncode(document.title),I18NRE):document.title; 
    } 
    WT.js="Yes"; 
    WT.jv=dcsJV(); 
    if (document.body&&document.body.addBehavior){ 
        document.body.addBehavior("#default#clientCaps"); 
        if (document.body.connectionType){ 
            WT.ct=document.body.connectionType; 
        } 
        document.body.addBehavior("#default#homePage"); 
        WT.hp=document.body.isHomePage(location.href)?"1":"0"; 
    } 
    if (parseInt(navigator.appVersion)>3){ 
        if ((navigator.appName=="Microsoft Internet Explorer")&&document.body){ 
            WT.bs=document.body.offsetWidth+"x"+document.body.offsetHeight; 
        } 
        else if (navigator.appName=="Netscape"){ 
            WT.bs=window.innerWidth+"x"+window.innerHeight; 
        } 
    } 
    WT.fi="No"; 
    if (window.ActiveXObject){ 
        for(var i=10;i>0;i--){ 
            try{ 
                var flash = new ActiveXObject("ShockwaveFlash.ShockwaveFlash."+i); 
                WT.fi="Yes"; 
                WT.fv=i+".0"; 
                break; 
            } 
            catch(e){ 
            } 
        } 
    } 
    else if (navigator.plugins&&navigator.plugins.length){ 
        for (var i=0;i<navigator.plugins.length;i++){ 
            if (navigator.plugins[i].name.indexOf('Shockwave Flash')!=-1){ 
                WT.fi="Yes"; 
                WT.fv=navigator.plugins[i].description.split(" ")[2]; 
                break; 
            } 
        } 
    } 
    if (gI18n){ 
        WT.em=(typeof(encodeURIComponent)=="function")?"uri":"esc"; 
        if (typeof(document.defaultCharset)=="string"){ 
            WT.le=document.defaultCharset; 
        }  
        else if (typeof(document.characterSet)=="string"){ 
            WT.le=document.characterSet; 
        } 
    } 
    WT.sp="@@SPLITVALUE@@"; 
    DCS.dcsdat=dCurrent.getTime(); 
    DCS.dcssip=window.location.hostname; 
    DCS.dcsuri=window.location.pathname; 
    if (window.location.search){ 
        DCS.dcsqry=window.location.search; 
        if (gQP.length>0){ 
            for (var i=0;i<gQP.length;i++){ 
                var pos=DCS.dcsqry.indexOf(gQP[i]); 
                if (pos!=-1){ 
                    var front=DCS.dcsqry.substring(0,pos); 
                    var end=DCS.dcsqry.substring(pos+gQP[i].length,DCS.dcsqry.length); 
                    DCS.dcsqry=front+end; 
                } 
            } 
        } 
    } 
    if ((window.document.referrer!="")&&(window.document.referrer!="-")){ 
        if (!(navigator.appName=="Microsoft Internet Explorer"&&parseInt(navigator.appVersion)<4)){ 
            DCS.dcsref=gI18n?dcsEscape(window.document.referrer, I18NRE):window.document.referrer; 
        } 
    } 
} 
 
function dcsA(N,V){ 
    return "&"+N+"="+dcsEscape(V, RE); 
} 
 
function dcsEscape(S, REL){ 
    if (typeof(REL)!="undefined"){ 
        var retStr = new String(S); 
        for (R in REL){ 
            retStr = retStr.replace(REL[R],R); 
        } 
        return retStr; 
    } 
    else{ 
        return escape(S); 
    } 
} 
 
function dcsEncode(S){ 
    return (typeof(encodeURIComponent)=="function")?encodeURIComponent(S):escape(S); 
} 
 
function dcsCreateImage(dcsSrc){ 
    if (document.images){ 
        gImages[gIndex]=new Image; 
        if ((typeof(gHref)!="undefined")&&(gHref.length>0)){ 
            gImages[gIndex].onload=gImages[gIndex].onerror=dcsLoadHref; 
        } 
        gImages[gIndex].src=dcsSrc; 
        gIndex++; 
    } 
    else{ 
        document.write('<IMG ALT="" BORDER="0" NAME="DCSIMG" WIDTH="1" HEIGHT="1" SRC="'+dcsSrc+'">'); 
    } 
} 
 
function dcsMeta(){ 
    var elems; 
    if (document.all){ 
        elems=document.all.tags("meta"); 
    } 
    else if (document.documentElement){ 
        elems=document.getElementsByTagName("meta"); 
    } 
    if (typeof(elems)!="undefined"){ 
        for (var i=1;i<=elems.length;i++){ 
            var meta=elems.item(i-1); 
            if (meta.name){ 
                if (meta.name.indexOf('WT.')==0){ 
                    WT[meta.name.substring(3)]=(gI18n&&(meta.name.indexOf('WT.ti')==0))?dcsEscape(dcsEncode(meta.content),I18NRE):meta.content; 
                } 
                else if (meta.name.indexOf('DCSext.')==0){ 
                    DCSext[meta.name.substring(7)]=meta.content; 
                } 
                else if (meta.name.indexOf('DCS.')==0){ 
                    DCS[meta.name.substring(4)]=(gI18n&&(meta.name.indexOf('DCS.dcsref')==0))?dcsEscape(meta.content,I18NRE):meta.content; 
                } 
            } 
        } 
    } 
} 
 
function dcsTag(){ 
    if (document.cookie.indexOf("WTLOPTOUT=")!=-1){ 
        return; 
    } 
    var P="http"+(window.location.protocol.indexOf('https:')==0?'s':'')+"://"+gDomain+(gDcsId==""?'':'/'+gDcsId)+"/dcs.gif?"; 
    for (N in DCS){ 
        if (DCS[N]) { 
            P+=dcsA(N,DCS[N]); 
        } 
    } 
    for (N in WT){ 
        if (WT[N]) { 
            P+=dcsA("WT."+N,WT[N]); 
        } 
    } 
    for (N in DCSext){ 
        if (DCSext[N]) { 
            P+=dcsA(N,DCSext[N]); 
        } 
    } 
    if (P.length>2048&&navigator.userAgent.indexOf('MSIE')>=0){ 
        P=P.substring(0,2040)+"&WT.tu=1"; 
    } 
    dcsCreateImage(P); 
} 
 
function dcsJV(){ 
    var agt=navigator.userAgent.toLowerCase(); 
    var major=parseInt(navigator.appVersion); 
    var mac=(agt.indexOf("mac")!=-1); 
    var nn=((agt.indexOf("mozilla")!=-1)&&(agt.indexOf("compatible")==-1)); 
    var nn4=(nn&&(major==4)); 
    var nn6up=(nn&&(major>=5)); 
    var ie=((agt.indexOf("msie")!=-1)&&(agt.indexOf("opera")==-1)); 
    var ie4=(ie&&(major==4)&&(agt.indexOf("msie 4")!=-1)); 
    var ie5up=(ie&&!ie4); 
    var op=(agt.indexOf("opera")!=-1); 
    var op5=(agt.indexOf("opera 5")!=-1||agt.indexOf("opera/5")!=-1); 
    var op6=(agt.indexOf("opera 6")!=-1||agt.indexOf("opera/6")!=-1); 
    var op7up=(op&&!op5&&!op6); 
    var jv="1.1"; 
    if (nn6up||op7up){ 
        jv="1.5"; 
    } 
    else if ((mac&&ie5up)||op6){ 
        jv="1.4"; 
    } 
    else if (ie5up||nn4||op5){ 
        jv="1.3"; 
    } 
    else if (ie4){ 
        jv="1.2"; 
    } 
    return jv; 
} 
 
function dcsFunc(func){ 
    if (typeof(window[func])=="function"){ 
        window[func](); 
    } 
} 
 
dcsVar(); 
dcsMeta(); 
dcsFunc("dcsAdv"); 
dcsTag(); 
//--> 
</SCRIPT> 
 
<NOSCRIPT> 
<IMG ALT="" BORDER="0" NAME="DCSIMG" WIDTH="1" HEIGHT="1" SRC="http://sdc.hns.com/dcsu659jtu379xril69y0rr8e_4z5q/njs.gif?dcsuri=/nojavascript&amp;WT.js=No"> 
</NOSCRIPT> 
<!-- END OF SmartSource Data Collector  TAG -->     
 
</body> 
  </html> 
```

---

### Post by coffeecat on 2010-11-05
> **muddpup64 said:**
> Here is the file you asked for:

I'm not surprised your package manager is choking on that. It's not a source file; it's an html file for a webpage. You must have made an error when you copied and pasted the code trikster_x posted for adding the Medibuntu repository.

First, open a terminal and do this command:

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

Be very careful typing that in. In fact, copy it with ctrl-C and then paste it into the terminal with ctrl-shift-V. That will remove the faulty medibuntu.list file. Now go to this page:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository)

Follow the instructions there. The code is the same as trikster_x posted but is presented better than this forum software allows. Copy and paste as before. Do not attempt to type it by hand. Make sure you have pasted the whole of those four lines into the terminal. Once you have followed those commands you will be able to install libdvdcss2 by doing:

```
sudo apt-get install libdvdcss2
```

---

### Post by muddpup64 on 2010-11-05
Thanks, worked like a charm.

---

### Post by nm_geo on 2010-11-11
Oh man how I love these forums.  I really never watch DVDs on my puter, but I like everything to work and following this link got me there too.  If I could mark this messages SOLVED I sure would thanks for all the help.  My Ubuntu experience just keeps getting better and I know it is the volunteer group that is doing it. 
:P

---

