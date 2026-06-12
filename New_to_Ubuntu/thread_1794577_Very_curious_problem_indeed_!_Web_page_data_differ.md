---
title: "Very curious problem indeed ! Web page data differs"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by zshanthi on 2011-07-01
Please note this happens only in in THIS particular webpage alone

When I access the webpage

[http://shopping.rediff.com/product/bushnell-powerview-x21-compact-folding-binoculars/10831962]("http://shopping.rediff.com/product/bushnell-powerview-x21-compact-folding-binoculars/10831962")

from windows using firefox and I view the page source I see the following code

```
            <div class="floatL product_detail">
              <div class="product_detail_top">
									Seller: <a href="http://pages.rediff.com/ojjas-enterprises/190903"><b>Ojjas Enterprises</b></a><span class="normal">( <a href="/shop/sellerinfo.jsp?vno=936" onClick="hidepopup()" target="_blank">Positive Feedback: 95%</a>)</span>
                <br>
                <s>MRP <font class="strike"><span id="prod_listpprc">Rs. 1,995</span></font>

                </s>
                <br><span class="webprz">Rs. <span class="cinch_price_amount webprz" property="v:price" product_id="10831962" id="prod_prcs" api_type="radon">999</span></span>
                <br>


```

But when I access the same webpage using GET or LYNX from ubuntu command line

I see the following code at the same location

```
  <div class="floatL product_detail">
              <div class="product_detail_top"><span class="normal"></span>
                <br><span class="webprz">Rs. <span class="cinch_price_amount webprz" property="v:price" product_id="" id="prod_prcs" api_type="radon"></span></span>
                <br>
```


Please note this cannot be any javascript or css script running on client side since I'm viewing the direct html source code in the browser and not any GENERATED source code

So how could this happen at all ?

I'm puzzled !

---

### Post by zshanthi on 2011-07-01
oh wait ! Just to be on an even keel, I accessed the same page from windows DOS prompt by running a perl LWP script and I am able to see the first source code and not the second. So definitely there is HTML  source code discrepancy in windows and ubuntu. My question is why ???:confused:

---

### Post by jtarin on 2011-07-01
```
            <div class="floatL product_detail">
              <div class="product_detail_top">
									Seller: <a href="http://pages.rediff.com/ojjas-enterprises/190903"><b>Ojjas Enterprises</b></a><span class="normal">( <a href="/shop/sellerinfo.jsp?vno=936" onClick="hidepopup()" target="_blank">Positive Feedback: 95%</a>)</span>
                <br>
                <s>MRP <font class="strike"><span id="prod_listpprc">Rs. 1,995</span></font>

                </s>
                <br><span class="webprz">Rs. <span class="cinch_price_amount webprz" property="v:price" product_id="10831962" id="prod_prcs" api_type="radon">999</span></span>
```This Ubuntu Firefox 5.0

---

### Post by zshanthi on 2011-07-01
Thanks. That explains it ..atleast partially.

Both browsers in windows and ubuntu display the same.

So why the perl lwp command line code in windows and ubuntu differ ?

IN windows command line I get the same output as you have got but in ubuntu I get differently ?

---

### Post by jtarin on 2011-07-01
Are you using Perl in Win and Ubuntu? If so then something about your Perl install in Ubuntu isn't parsing some html......links for one.

---

### Post by zshanthi on 2011-07-01
yes  both in windows and ubuntu

the SAME code in both locations but different outputs

```


use strict;
use warnings;
use WWW::Mechanize;
use Storable;
my $url = "http://shopping.rediff.com/product/bushnell-powerview-x21-compact-folding-binoculars/10831962";
    my $mech = WWW::Mechanize->new( autocheck => 1);
 $mech->get($url);
   my $c = $mech->content();
print $c;


```

---

### Post by zshanthi on 2011-07-01
> **jtarin said:**
>  If so then something about your Perl install in Ubuntu isn't parsing some html......links for one.

I think you are very near the problem/solution. So what could it be ? I receive no error messages?

---

### Post by jtarin on 2011-07-01
My Perl's too rusty it's been some years......[try this site and link]("http://lwp.interglacial.com/ch04_01.htm") and maybe something will shout out at you.

---

### Post by zshanthi on 2011-07-01
Also it is not only about perl, suppose if you run in command line


```

GET "http://shopping.rediff.com/product/bushnell-powerview-x21-compact-folding-binoculars/10831962"

```
OR
```

LYNX "http://shopping.rediff.com/product/bushnell-powerview-x21-compact-folding-binoculars/10831962"


```

The same issue happens. Some parts of html are missing .

---

### Post by jtarin on 2011-07-01
GET/Ubuntu```
 <div class="floatL product_detail">
              <div class="product_detail_top">
									Seller: <a href="http://pages.rediff.com/ojjas-enterprises/190903"><b>Ojjas Enterprises</b></a><span class="normal">( <a href="/shop/sellerinfo.jsp?vno=936" onClick="hidepopup()" target="_blank">Positive Feedback: 95%</a>)</span>
                <br>
                <s>MRP <font class="strike"><span id="prod_listpprc">Rs. 1,995</span></font>
                </s>
                <br><span class="webprz">Rs. <span class="cinch_price_amount webprz" property="v:price" product_id="10831962" id="prod_prcs" api_type="radon">999</span></span>
```

---

### Post by Nytram on 2011-07-01
My guess would be that the page is being built dynamically on the server side, and differs depending on the user agent/browser.

---

### Post by jtarin on 2011-07-01
Not necessarily so as you can see by comparisons.

---

