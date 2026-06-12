---
title: "Can't open package manager"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by AVS0197 on 2010-06-21
I tried to install playonlinux on ubuntu 10.04 using what I later realized was an old method and now can't open package manager... when I try I get the following error:

"E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."


I did a search and found in this thread someone (not the original thread poster) had a similar problem

[http://ubuntuforums.org/showthread.php?t=855267](http://ubuntuforums.org/showthread.php?t=855267)

I tried doing what was suggested in the last post and this is the error I got:

"cat: etc/apt/sources.list.d/playonlinux.list: No such file or directory"

Does anyone have any suggestions as to what I can do to fix this? I know it says something in the original error about the repository dialog but I have no clue what that is

---

### Post by snowpine on 2010-06-21
You're missing a / symbol, try:

```
cat /etc/apt/sources.list.d/playonlinux.list
```

---

### Post by AVS0197 on 2010-06-21
> **snowpine said:**
> You're missing a / symbol, try:

```
cat /etc/apt/sources.list.d/playonlinux.list
```

Thanks that worked, here is what came up:

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<!-- turing_cluster_prod -->
<html>
<head> <title>  mulx.net  </title>
<meta http-equiv="Keywords" content="">
<meta http-equiv="Description" content="">
<meta http-equiv="Content-Type" content="text/html;charset=utf-8">
<link rel="shortcut icon" href="http://spi.domainsponsor.com/favicon/mi_favicon.ico" type="image/x-icon"> 
  <script type="text/javascript">
    
      
    
    var flagsloaded = false;

  function loadFlags () {
      if ( !flagsloaded ) {
          var listel = document.getElementById( "dropdownflag" );   listel.options[0].style.background =  "url('http://spi.domainsponsor.com/images/en.png') no-repeat right";  listel.options[1].style.background =  "url('http://spi.domainsponsor.com/images/es.png') no-repeat right";  listel.options[2].style.background =  "url('http://spi.domainsponsor.com/images/fr.png') no-repeat right";  listel.options[3].style.background =  "url('http://spi.domainsponsor.com/images/zh.png') no-repeat right";  listel.options[4].style.background =  "url('http://spi.domainsponsor.com/images/de.png') no-repeat right";  listel.options[5].style.background =  "url('http://spi.domainsponsor.com/images/pt.png') no-repeat right";  listel.options[6].style.background =  "url('http://spi.domainsponsor.com/images/ja.png') no-repeat right";  listel.options[7].style.background =  "url('http://spi.domainsponsor.com/images/nl.png') no-repeat right";  listel.options[8].style.background =  "url('http://spi.domainsponsor.com/images/it.png') no-repeat right";  listel.options[9].style.background =  "url('http://spi.domainsponsor.com/images/ko.png') no-repeat right";  flagsloaded = true;
      }
  }  function addEvent(obj, evType, fn) { 
        if (obj.addEventListener){ 
            obj.addEventListener(evType, fn, false); 
            return true; 
        } else if (obj.attachEvent){ 
            var r = obj.attachEvent("on"+evType, fn); 
            return r; 
        } else { 
            return false; 
        } 
    }  function addOToken( elm ) {
  var allLinks = document.getElementsByTagName('a');
    for( var j=0; j < allLinks.length; j++ ){
        if ( allLinks.item(j).className.match("kw") ) {
            allLinks.item(j).setAttribute('href', allLinks.item(j).href+"&ot="+elm);
        }
    }

    if ( document.getElementById( 'searchbox_action' ) ) {
        var ot_elm = document.createElement( 'INPUT' );
        ot_elm.value = elm;
        ot_elm.type= 'hidden';
        ot_elm.name = 'ot';
        ot_elm.id = 'ot';
        document.getElementById('searchbox_action').getElementsByTagName('DIV')[0].appendChild( ot_elm );
    }
}
  </script>  

    
        <link rel="stylesheet" href="http://spi.domainsponsor.com/css/0/landing/en.css" type="text/css">
        
        
        <link rel="stylesheet" href="http://spi.domainsponsor.com/css/501/landing/en.css" type="text/css">
        
         
</head>

<body onunload="exitPop();" class='generic'>
<div id="container">
    <div class="container_wrap">

<!-- BOF Header -->
    <div id="header">  <div id="header_wrap">
    <div id="header_title">   <h1 id="domainname"> Mulx.net </h1>
        <p id="tagline">  What you need, when you need it  <p>  </div>

    <div id="header_links">  <div class="links_wrap">  <div class="dropdown"> <form action="/" method="POST" name="lang_selection" id="lang_dropdown">
        <div class="lang_dropdown_wrap">
            <input type="hidden" name="epl" value="02870087VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1tXTGtTCVpXCV1dWBVRD0QQDEgcWwNPBFcEUQARFQRGQWdRUAxTBQBESFYWWkAIXwxeSwAHQQJcOVUMTREOEUEIV1YSQQpFQQxcXBcOWwdWRAddFg9UD2sPU14AB1BHVlRMXVNeF0wJBV1XAEFdAhYRD1EGA2wIUFsBRUZSABNWXWdMTUEACFINSlRDUlgNXxU8XwoJVA1ROV0QCAc">
            <input type="hidden" name="debug" value="0">
            <select id="dropdownflag" name="dropdown_lang" onchange="this.form.submit()" onclick="loadFlags();">  <option value="en" selected> English </option>  <option value="es" > Español </option>  <option value="fr" > Français </option>  <option value="zh" > &#20013;&#25991; </option>  <option value="de" > Deutsch </option>  <option value="pt" > Português </option>  <option value="ja" > &#26085;&#26412;&#35486; </option>  <option value="nl" > Nederlands </option>  <option value="it" > Italiano </option>  <option value="ko" > &#54620;&#44397;&#50612; </option>  </select>
        </div>
    </form> </div>   <p id="date"> June 21, 2010       </p>  </div>   <p id="links"> <a href="#" onclick="window.external.AddFavorite('http://www.mulx.net','mulx.net');" class="link_bookmark">Bookmark this page</a> <a href="#" onclick="this.style.behavior='url(#default#homepage)';this.setHomePage('http://www.mulx.net');" class="link_homepage">Make this your homepage</a>  </p>  </div>
    <div class="clear">&nbsp;</div>
</div>  <div class="top_break"></div>    </div>
<!-- EOF Header -->

<!-- BOF Main -->
    <div id="main">
        <div class="main_wrap">

<!-- BOF Sidebar -->
        <div id="sidebar">
            <div class="sidebar_wrap">       </div>
        </div>
<!-- EOF Sidebar -->

<!-- BOF Keywords -->
        <div id="content">
            <div class="content_wrap"> <a class="kw" onclick="doPop=0;" href='/?epl=02800072VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1tXTGtTCVpXCV1dWBVRD0QQDEgcWwNPBFcEUQARFQRGQWdRUAxTBQBEV0kRDlsPFhIMSBAIVwRGW1gFUxESBFRHW1BrQQpGCQBXTUNXURJZBQ1nDAIOVARXEQBUQwQGWkdBBVNUC1BGC1sfFl9dAlU9ClxYUBUSUQdFAF1oFRhFUAVUXV8OE1UOVFYSbFMOXwUPXToMQFwE&query=botsearch09' style="display: none">stock photo</a>     <!-- BOF popmain -->
    <div class="popmain">   <div class="popmain_wrap">
        <div class="popmain_left">&nbsp;</div>
        <div class="popmain_center">
          <span class="text_related">Related Searches</span> <ul id='popmain_kw_0'>                      <li class="kwl_1">                              <a href='/?epl=03630008VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNU0VLAAdBAlw5RwxGChEORUBUWUZuCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhRS1dERVZqBERLVQxQUT5ZBl4OQxVWAEYFXzxBThEECFlRVl8XBFlYDU9mAlxbBlwHPFIWWwM&amp;query=stock%20photo' onclick='doPop=0;' class='kw '>stock photo</a>   </li>             <li class="kwl_2">                              <a href='/?epl=03630029VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNUEVLAAdBAlw5RwxGChEORUBUWUZuCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhRS1dERVZqBERLVQxQUT5ZBl4OQxVWAEYFXzxBThEECFlRVl8XBFlYDU9mAlxbBlwHPFIWWwM&amp;query=free%20downloads' onclick='doPop=0;' class='kw '>free downloads</a>   </li>             <div class="clear">&nbsp;</div>  </ul>            <ul id='popmain_kw_1'>                      <li class="kwl_3">                              <a href='/?epl=03630045VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNUUVLAAdBAlw5RwxGChEORUBUWUZuCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhRS1dERVZqBERLVQxQUT5ZBl4OQxVWAEYFXzxBThEECFlRVl8XBFlYDU9mAlxbBlwHPFIWWwM&amp;query=credit%20card' onclick='doPop=0;' class='kw '>credit card</a>   </li>             <div class="clear">&nbsp;</div>  </ul>            <ul id='popmain_kw_2'>                      <li class="kwl_4">                              <a href='/?epl=03630068VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNVkVLAAdBAlw5RwxGChEORUBUWUZuCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhRS1dERVZqBERLVQxQUT5ZBl4OQxVWAEYFXzxBThEECFlRVl8XBFlYDU9mAlxbBlwHPFIWWwM&amp;query=debt%20reduction' onclick='doPop=0;' class='kw '>debt reduction</a>   </li>             <div class="clear">&nbsp;</div>  </ul>            <ul id='popmain_kw_3'>                      <li class="kwl_5">                              <a href='/?epl=03630009VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNV0VLAAdBAlw5RwxGChEORUBUWUZuCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhRS1dERVZqBERLVQxQUT5ZBl4OQxVWAEYFXzxBThEECFlRVl8XBFlYDU9mAlxbBlwHPFIWWwM&amp;query=stock%20image' onclick='doPop=0;' class='kw '>stock image</a>   </li>             <div class="clear">&nbsp;</div>  </ul>            <ul id='popmain_kw_4'>                      <li class="kwl_6">                              <a href='/?epl=03630030VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNVEVLAAdBAlw5RwxGChEORUBUWUZuCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhRS1dERVZqBERLVQxQUT5ZBl4OQxVWAEYFXzxBThEECFlRVl8XBFlYDU9mAlxbBlwHPFIWWwM&amp;query=car%20insurance' onclick='doPop=0;' class='kw '>car insurance</a>   </li>             <li class="kwl_7">                              <a href='/?epl=03630046VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNVUVLAAdBAlw5RwxGChEORUBUWUZuCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhRS1dERVZqBERLVQxQUT5ZBl4OQxVWAEYFXzxBThEECFlRVl8XBFlYDU9mAlxbBlwHPFIWWwM&amp;query=mortgage%20loan' onclick='doPop=0;' class='kw '>mortgage loan</a>   </li>             <li class="kwl_8">                              <a href='/?epl=03630069VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNWkVLAAdBAlw5RwxGChEORUBUWUZuCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhRS1dERVZqBERLVQxQUT5ZBl4OQxVWAEYFXzxBThEECFlRVl8XBFlYDU9mAlxbBlwHPFIWWwM&amp;query=personal%20loans' onclick='doPop=0;' class='kw '>personal loans</a>   </li>             <li class="kwl_9">                              <a href='/?epl=03630010VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNW0VLAAdBAlw5RwxGChEORUBUWUZuCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhRS1dERVZqBERLVQxQUT5ZBl4OQxVWAEYFXzxBThEECFlRVl8XBFlYDU9mAlxbBlwHPFIWWwM&amp;query=mutual%20funds' onclick='doPop=0;' class='kw '>mutual funds</a>   </li>             <div class="clear">&nbsp;</div>  </ul> </div>
        <div class="popmain_right">&nbsp;</div>
      </div>  <div class="clear">&nbsp;</div>
    </div>

    <div class="clear">&nbsp;</div>
<!-- EOF popmain -->    <!-- BOF popmain generic -->
    <div class="popmain_generic"> <!-- BOF popgeneric -->  <ul class="cat_favorite">  <li class="header">  Popular Categories  </li>                    <li>    <a href='/?epl=03460017VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1tXTGtTCVpXCV1dWBVRD0QQDEgcWwNPBFcEUQARFQRGQWdRUAxTBQBEV0kRDlsPFhIMSBAIVwRGW1gFUxEKFmpHWVZfDFUTRwdZSwZbaxFfEV5fAAhWE10FaA5UXg8_WVRWXF1fAhNQB0tQAl1rCFRfVghUQFAAQANQDEdOXAZQW11KXVJDXlEbT1YXV2sSXxcRWwBbUABAOVoWE0QNCFZQZ1FQDFMTRwdZSwZbaxVJEgYFCQ9dChIHWw9aQD4GWlpfVFFuD0YJUg&query=Travel' onclick='doPop = 0;'  class='kw '    >Travel</a>    <ul class="sub">      <li class="kwl_1">                              <a href='/?epl=03600046VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNU0VLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=Airline%20tickets' onclick='doPop=0;' class='kw '>Airline tickets</a>   </li>                         <li class="kwl_2">                              <a href='/?epl=03600067VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNUEVLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=Hotels' onclick='doPop=0;' class='kw '>Hotels</a>   </li>                         <li class="kwl_3">                              <a href='/?epl=03600083VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNUUVLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=Car%20rental' onclick='doPop=0;' class='kw '>Car rental</a>   </li>                         <li class="kwl_4">                              <a href='/?epl=03600007VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNVkVLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=Flights' onclick='doPop=0;' class='kw '>Flights</a>   </li>                         <li class="kwl_5">                              <a href='/?epl=03600047VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNV0VLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=South%20Beach%20Hotels' onclick='doPop=0;' class='kw '>South Beach Hotels</a>   </li>  </ul>     </li>              <li>    <a href='/?epl=03460017VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1tXTGtTCVpXCV1dWBVRD0QQDEgcWwNPBFcEUQARFQRGQWdRUAxTBQBEV0kRDlsPFhIMSBAIVwRGW1gFUxEKFmpHWVZfDFUTRwdZSwZbaxFfEV5fAAhWE10FaA5UXg8_WVRWXF1fAhNQB0tQAl1rCFRfVghUQFAAQANQDEdOXAZQW11KXVJDXlEbT1YXV2sSXxcRWwBbUABAOVoWE0QNCFZQZ1FQDFMTRwdZSwZbaxVJEgYFCQ9dChIHWw9aQD4GWlpfVFFuD0YJUg&query=Finance' onclick='doPop = 0;'  class='kw '    >Finance</a>    <ul class="sub">      <li class="kwl_1">                              <a href='/?epl=03600046VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNU0VLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=Free%20credit%20report' onclick='doPop=0;' class='kw '>Free credit report</a>   </li>                         <li class="kwl_2">                              <a href='/?epl=03600067VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNUEVLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=Online%20Payment' onclick='doPop=0;' class='kw '>Online Payment</a>   </li>                         <li class="kwl_3">                              <a href='/?epl=03600083VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNUUVLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=Credit%20Card%20Application' onclick='doPop=0;' class='kw '>Credit Card Application</a>   </li>                         <li class="kwl_4">                              <a href='/?epl=03600007VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNVkVLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=Car%20Insurance' onclick='doPop=0;' class='kw '>Car Insurance</a>   </li>                         <li class="kwl_5">                              <a href='/?epl=03600047VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNV0VLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=Health%20insurance' onclick='doPop=0;' class='kw '>Health insurance</a>   </li>  </ul>     </li>              <li>    <a href='/?epl=03460017VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1tXTGtTCVpXCV1dWBVRD0QQDEgcWwNPBFcEUQARFQRGQWdRUAxTBQBEV0kRDlsPFhIMSBAIVwRGW1gFUxEKFmpHWVZfDFUTRwdZSwZbaxFfEV5fAAhWE10FaA5UXg8_WVRWXF1fAhNQB0tQAl1rCFRfVghUQFAAQANQDEdOXAZQW11KXVJDXlEbT1YXV2sSXxcRWwBbUABAOVoWE0QNCFZQZ1FQDFMTRwdZSwZbaxVJEgYFCQ9dChIHWw9aQD4GWlpfVFFuD0YJUg&query=Home' onclick='doPop = 0;'  class='kw '    >Home</a>    <ul class="sub">      <li class="kwl_1">                              <a href='/?epl=03600046VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNU0VLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=Foreclosures' onclick='doPop=0;' class='kw '>Foreclosures</a>   </li>                         <li class="kwl_2">                              <a href='/?epl=03600067VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNUEVLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=Houses%20For%20Sale' onclick='doPop=0;' class='kw '>Houses For Sale</a>   </li>                         <li class="kwl_3">                              <a href='/?epl=03600083VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNUUVLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=Mortgage' onclick='doPop=0;' class='kw '>Mortgage</a>   </li>                         <li class="kwl_4">                              <a href='/?epl=03600007VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNVkVLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=People%20Search' onclick='doPop=0;' class='kw '>People Search</a>   </li>                         <li class="kwl_5">                              <a href='/?epl=03600047VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1pKUVNuF1RaCQUfC1xAPlIODFsOA1dcEgNZF0dYERgIBRYIBQJXABIWXUoRbF0FDVRTDEMJQxUJCVlFRVgRFFtRXUoJXgNTEglPZhdSWgoNV0VLAAdBAlw5RwxGCgYEW1BKUVduCFRdDGdVBF1QCF4FRVwAFVoGWjleBwgCUVATVllMUVYKR01fX1wLVkYIU0QIXRwRXBNQOUQMQEUCBAhWWUxrXBATRw5RWgBsXQUNVEVLAAdBAlw5QxpFUlwNXFtTHlVdCVpDPV9WClRYBG8IEAVV&amp;query=Real%20Estate%20Training' onclick='doPop=0;' class='kw '>Real Estate Training</a>   </li>  </ul>     </li>   </ul>
  <div class="clear">&nbsp;</div>
<!-- EOF popgeneric --> </div>
        <div class="clear">&nbsp;</div>
<!-- EOF popmain generic -->    </div>
        </div>
<!-- EOF Keywords -->
        <div class="clear">&nbsp;</div>

        </div>
    </div>
<!-- EOF Main -->

<!-- BOF Footer -->  <div id="footer">  <div class="search"> <div class="search_box">
  <form id="searchbox_action" action="/" method="POST" onSubmit="doPop = 0;" >
    <div>
    <input type="hidden" name="epl" value="03340032VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1tXTGtTCVpXCV1dWBVRD0QQDEgcWwNPBFcEUQARFQRGQWdRUAxTBQBEV0kRDlsPFhIMSBAIVwRGW1gFUxESBFRHW1BrQQpGCRFdWBdQXD5SDRtnCQddBV0IUEVRUhIIUltnUVAMUAUFRFtYEVZTDkIbXl8ACFYTXQURCFBOFg5HUWdLW0QXVlFfS1wEQVcJUg0bHhYKWgJROV4HCAFHElBUSltcbhFMRAcFXwpBWUdRDg9XEjlUDlsBWwZqXRJcBQ">
    <input type="hidden" name="debug" value="0">
    <input type="hidden" name="search_token" id="search_token" value="">
    <input type="hidden" name="click_token" id="click_token" value="">  <label>Search:</label>  <input type="text" name="query" class="text" value="">  <div class="submit_wrap">
        <input type="submit" value="Search" class="submit">
        </div>  </div>
  </form>
</div> </div>    <div class="footer_wrap">         <span class="footer_privacy_section">
        <a href="http://spi.domainsponsor.com/t/privacy_ds.htm" target="privacy_mulx_net">Privacy Policy</a>
        </span>    </div>   </div>  <!-- EOF Footer -->

    </div>
</div> <div class="sub_wrap" id="placeholder">     <img src="/?epl=03020062VGsLXARdBQRSBUQHVwgHWg9aB1oGCFoUDU0bVl1AFwJaWz1KXANWRgRCX0VMFlsCUwNRBlcEBVNRE1tXTGtTCVpXCV1dWBVRD0QQDEgcWwNPBFcEUQARFQRGQWdRUAxTBQBESFYWWkAIXwxeSwAHQQJcOVUMTREOEUEIV1YSQQpFQQxcXBcOWwdWRBNQBBVWXFgJVgcTUwQSXFJWZ11VWAAEUx5aBEdRBl8QGgUCA10ERg9URUZbCAJQalFcCQdDRlEDSloNbEAYQAdeXgoUXkdVClsMQmgGDlpSVF1rWxYIBA" height="1" width="1" alt="">   <script type='text/javascript'>   </script>    <iframe src='http://domdex.com/f?c=107' width=0 height=0 frameborder=0></iframe>       <script type="text/javascript">
//<!--
var doPop = 1;
function exitPop() {
    if (doPop) {  }
}
//-->
</script>  </div> <!-- Design ID 501 -->
<!-- Slice ID 6 -->
<!-- Test ID 604 -->
<!-- page_complete -->
</body>

```

Does this tell you anything? I really wasn't expecting something huge like that lol

---

### Post by lkjoel on 2010-06-21
If you are trying to install PlayonLinux, I would suggest that you should add this line to your /etc/apt/sources.list file before installing it.
```
deb http://deb.playonlinux.com/ lucid main
```

---

### Post by snowpine on 2010-06-21
> **AVS0197 said:**
> Thanks that worked, here is what came up:

Does this tell you anything? I really wasn't expecting something huge like that lol

You created a garbage file for some bizarre reason. Delete it with:

```
sudo rm /etc/apt/sources.list.d/playonlinux.list
```

In the future, be more careful editing system files outside your /home folder. :)

---

### Post by AVS0197 on 2010-06-21
> **snowpine said:**
> You created a garbage file for some bizarre reason. Delete it with:

```
sudo rm /etc/apt/sources.list.d/playonlinux.list
```In the future, be more careful editing system files outside your /home folder. :)

lol yeah I was following instructions from a site (as it was the site I heard about playonlinux from) and then realized when I messed everything up that the instructions were 2 years old

Thanks alot! This worked and I should be good to go now!


> If you are trying to install PlayonLinux, I would suggest that you  should add this line to your /etc/apt/sources.list file before  installing it.

That was what I was trying to do and thanks!

---

### Post by lkjoel on 2010-06-21
No problem, does it work?

---

### Post by AVS0197 on 2010-06-21
> **lkjoel said:**
> No problem, does it work?

Seems to be...been waiting for it to download updates for a long time but that's probably just my connection sucking lol

---

### Post by lkjoel on 2010-07-05
If you want a faster way to download updates, try:
```
sudo apt-get update
sudo apt-get upgrade
```

---

