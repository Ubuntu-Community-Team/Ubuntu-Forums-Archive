---
title: "Ram Slots"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by mistypaw on 2010-03-26
I want to put Ubuntu on a old laptop that I have. Said laptop is a Gateway Solo 5300. The specs are here: [http://support.gateway.com/s/manlib/Notebooks/Solo5300/8508144/8508144.htm](http://support.gateway.com/s/manlib/Notebooks/Solo5300/8508144/8508144.htm)

And CPU-Z says:
> 
DMI Physical Memory Array    
    location    Motherboard
    usage    System Memory
    correction    None
    max capacity    1024 MBytes
    max# of devices    2

DMI Memory Device    
    designation    J2
    format    SODIMM
    type    SDRAM
    total width    64 bits
    data width    64 bits
    size    128 MBytes

DMI Memory Device    
    designation    J3
    format    SODIMM
    type    SDRAM
    total width    64 bits
    data width    64 bits
    size    128 MBytes

I was thinking of getting 2 256 PC100 SDRAMs. If that's the right thing to get. Would that be enough? How much more could/should I do?

---

### Post by Bradtek on 2010-03-26
> max capacity 1024 MBytes

1024 MBytes = 1Gb = Much better

512 will work but ........

---

### Post by mistypaw on 2010-03-26
Also, how concerned need I be with the pin count? the specs page says "[FONT=Verdana, Arial, Helvetica, sans-serif][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]Two                      144-pin industrial standard SO-DIMM sockets" - but nothing on ebay says anyting about that. And the pins all seem to be 168 that i'm seeing.
[/SIZE][/FONT][/FONT]

---

### Post by mistypaw on 2010-03-26
ok, i just opened up the back to physically look at what was there (a bit of a scarey thing for me).. and these look totally different than anything i'm seeing online. i can post a pic later... but i think the pin count and those side bracket thingies are defiantly important from the looks of it.

---

### Post by oldsoundguy on 2010-03-26
Crucial says: ([www.crucial.com](www.crucial.com))
[http://www.crucial.com/store/listparts.aspx?model=Solo%205300%20Series](http://www.crucial.com/store/listparts.aspx?model=Solo%205300%20Series)

That gives you the model number.  Don't have to buy from them, but they are one of the best.

Note .. max for that laptop is 512.

---

### Post by mistypaw on 2010-03-26
I think i've almost got this figured out. (Yay, and it's 3:30 am!)

If i can just figure out if I should have pc100 or pc133 (I have one of each in there now). crucial says pc133, and the gateway site said pc100.

Also, is it high or low density.

I figure these things out and I think I will know what to get.

---

### Post by cascade9 on 2010-03-26
186pin RAM is desktop, 144pin is SO-DIMM (laptop memory) There is no way to run 168pin SD RAM in a 144pin SO-DIMM slot. 

There are still PC-100 SO-DIMMs around, but you pay more for them- 

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010170381+1052907865&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=381&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010170381+1052907865&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=381&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

$32 for 256MB PC-133, $49 (!!!) for 256MB PC-100. 

You migth eb able to use PC-133 on that laptop, but there is no way to know for sure without trying it. Yes, I know he manufacturer say 'only PC-100' but I've seen other hardware that said the same thing and worked with PC-133.  

> **oldsoundguy said:**
> Crucial says: ([www.crucial.com]("http://www.crucial.com"))
[http://www.crucial.com/store/listparts.aspx?model=Solo%205300%20Series](http://www.crucial.com/store/listparts.aspx?model=Solo%205300%20Series)

That gives you the model number.  Don't have to buy from them, but they are one of the best.

Note .. max for that laptop is 512.

Oddly enough, that laptop must be using the desktop ZX chipset, not the mobile version- ZX-M (mobile) has a max memory of 256MB.

---

### Post by oldsoundguy on 2010-03-26
quit scratching your head and click on that crucial.com link above. (Crucial is Micron memory)
It is a way to figure out EXACTLY what you need .. it is a memory calculator .. you plug in the make and model of your computer (almost every computer known to man or every motherboard manufactured) and it spits out what the MANUFACTURER specifies works for YOUR computer.
In your case PC133.

---

### Post by JKyleOKC on 2010-03-26
> **mistypaw said:**
> I think i've almost got this figured out. (Yay, and it's 3:30 am!)

If i can just figure out if I should have pc100 or pc133 (I have one of each in there now). crucial says pc133, and the gateway site said pc100.

Also, is it high or low density.

I figure these things out and I think I will know what to get.The 100 and 133 refer to the maximum clock speed that the stick can work at. In almost every case, a PC133 stick will work in a machine that calls for PC100, but the reverse is not necessarily true. Mixing them as you have done isn't the greatest of ideas, but if they are working I wouldn't worry about the mismatch.

More important, with older machines, is whether it needs low density or high density sticks. I learned the hard way that when the machine was built for low density memory, a high density stick won't do what you expect. In my case, I got only half the rated capacity: 256-MB sticks gave me only 128 MB each. And that was in a Gateway desktop system from the mid-1990s, so if your machine is equally old, it probably wants low-density sticks. The "maximum RAM" rating of 512 MB tends to bear this out as well.

---

### Post by mistypaw on 2010-03-26
Gateway says to use only PC100, and that  If PC133 memory is used, windows  protection errors will occur. I don't know how that would effect Ubutu though.

I didn't put one of each like that - it came that way and I'm only now realizing it.

I also read that as a rule of thumb if your processor speed is under 1000MB, go with low density. I don't know how reliable that is, but there is also someone on ebay selling high density 256MB PC100 144pins and they say it's not compatible.

---

### Post by oldsoundguy on 2010-03-26
C'mon now .. I fix computers as an avocation.  I use the memory calculator at Crucial all the time and have yet had any issues.  Sometimes their prices are lower than others, but I will USUALLY go for the same stick(s) in Kingston as their warranty is for whatever FOREVER.  They have never questioned an RMA for memory .. just sent a new one to replace a bad one.

But IF you want to continue to chase your tail over this simple thing .. go ahead.  I thought  my suggestion would solve your problem.

---

### Post by cascade9 on 2010-03-27
> **JKyleOKC said:**
> The 100 and 133 refer to the maximum clock speed that the stick can work at. In almost every case, a PC133 stick will work in a machine that calls for PC100, but the reverse is not necessarily true. Mixing them as you have done isn't the greatest of ideas, but if they are working I wouldn't worry about the mismatch.

I've seen machines that would have total failure to boot with PC-133 sticks, but worked fine with PC-100. (Intel LX and Ali Magic chipsets mainly)

> **oldsoundguy said:**
> C'mon now .. I fix computers as an avocation.  I use the memory calculator at Crucial all the time and have yet had any issues.  Sometimes their prices are lower than others, but I will USUALLY go for the same stick(s) in Kingston as their warranty is for whatever FOREVER.  They have never questioned an RMA for memory .. just sent a new one to replace a bad one.

But IF you want to continue to chase your tail over this simple thing .. go ahead.  I thought  my suggestion would solve your problem.

Same here, I build/fix computers, and you've been lucky IMO. Like I said above, I've seen issues with PC-133 not working. 

I think it should work, but to think you will never have any problems with PC-133 when PC-100 is speced is just wrong. 

If mistypaw did order PC-133 from crucial and it didnt work in that computer, thye should RMA it, they are good like that.

---

