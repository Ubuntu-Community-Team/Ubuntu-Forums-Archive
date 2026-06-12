---
title: "Help needed... Grease monkey, xpath, firebug"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by Ludwig3 on 2011-04-17
script:

From firbug xpath on the button is as follows:

.//*[@id='ctl00_mainContentPlaceholder_Button3']

and the script piece is:

<br>
     <input name="ctl00$mainContentPlaceholder$Button3" value="Back  To Auctions" onclick="closePopup(); return false;"  id="ctl00_mainContentPlaceholder_Button3" class="simplemodal-close"  style="width:160px;" type="submit">&nbsp;
<br>


my GM script is as follows...if theres mistakes, pls hlp, im new on java an gm, and dont know how to debug it.


// @include    *
// @version        0.1
// @description    Automatically click // ==/UserScript==




click_popupBtn1 = function() {

    var joinBtn=document.evaluate('//*[@id, "ctl00_mainContentPlaceholder_Button3"]'
,document,
 null,
 XPathResult.ORDERED_NODE_SNAPSHOT_TYPE,
 null).singleNodeValue.click();
alert(joinBtn);
    if(!joinBtn) return false;
    joinBtn.click();
    return true;
}


click_popupBtn1 ();


***ok,  here is the story...., im a newb in gm, and my last programming was 15  years ago on Tp. Ive discovered this auction site, which i want to  automate with GM.
there is 2 scr shots.  [http://www.mediafire.com/?lwy7agybtfn2x](http://www.mediafire.com/?lwy7agybtfn2x)     first scr shot, basic overview of site, with bidding buttons.
second overview, winnings popup
what i need to do...
i  need some help first to get rid of the popup... if its there i cant  bid. i used a similar script for the login page, and managed to get gm  to auto login, cause the server needs you to log in every 3 hrs or  so.see above mentioned scripts and xpath... ive tried, but my gm script  piece doesnt click on it...
then the project... i would like to do some of it myself, but i need some pointers...
on the attached txt file, auction1.txt, ive copied some of fire bugs console files, which look like :


*GET [http://www.xxx.xxx/REST_Service/REST_Au ... 3059143094]("http://www.xxx.xxx/REST_Service/REST_Auction.svc/GetAuctionData?_=1303059143094")
    
200 OK
        29.62s    
firebu...rver.js (line 169)
<System>
ParamsHeadersResponse
{"d":[["","","y","ZAR","1","33713","8887,  8887, 8887, 8887,  8887",null,"1.26","8887","0:13:30","","12","","C","29",null],["","","y","ZAR","2","34029","",null,"0.76","NONE","0:10:37","","5","","L",null,null],["","","y","ZAR","3","30332","3616,  9390, 9841, 8664,  4901",null,"379.80","3616","0:01:09","","1100","","T",null,null],["","","y","ZAR","4","33987","3616,  9168, 0605, 9168,  8771",null,"1.26","3616","0:00:51","","12","","T",null,null],["","","y","ZAR","5","34030","",null,"0.76","NONE","0:12:28","","5","","L",null,null],["y","-00:00","y","ZAR","6","34028","1137,  1137, 1137,  1137",null,"2.64","1137","0:20:05","","12","","L","12","vkSaGLYmZD+vgphl90foiM+3QXDf0c7SRfpMnt9PSDw="],["","","y","ZAR","7","33938","3616,   3616",null,"5.60","3616","0:01:50","","55","","T",null,null],["","","y","ZAR","8","33729","3616,  6197, 3616, 6197,  9134",null,"3.34","3616","0:01:26","","29","","T",null,null],["","","y","ZAR","9","33867","1551,   7243",null,"1.73","1551","0:02:40","","10","","B",null,null],["","","y","ZAR","10","33293","1551,  7243, 7243, 7243,  7243",null,"3.43","1551","0:06:10","","10","","B",null,null],["","","y","ZAR","11","33174","7243,  4901, 3614, 0481,  0481",null,"3.71","7243","0:06:10","","10","","B",null,null]]}
GET [http://www.xxx.xxx/REST_Service/REST_Au ... 059144766*]("http://www.xxx.xxx/REST_Service/REST_Auction.svc/GetAuctionData?_=1303059144766*")
    
from  there i can see all the info i need, and it is updated each second, so  in order for me to tell the GM script to bid on which button, i need to  get that information into the script to be processed... does anyone hav  any ideas?
i was thinking in the line of writing a small script for  each of the 12 small auctions, each handling its own part, collecting  its own info... i was thinkin those responses frm firebug can be usefull  and more direct way of getting info, that to go and subtract them one  by one from the windows, which is updated afterwards...
Can someone please give me some hlp...
Thanks..
regards
Ludwig

---

