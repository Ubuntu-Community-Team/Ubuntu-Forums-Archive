---
title: "Keyboard layout question!"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by tzarskielit on 2010-07-14
Hi guys, I need to access two Cyrillic letters which are now removed from the 'official' Bulgarian alphabet. 
[http://en.wikipedia.org/wiki/Yat](http://en.wikipedia.org/wiki/Yat) and [http://en.wikipedia.org/wiki/Little_Yus](http://en.wikipedia.org/wiki/Little_Yus)

It will be a vigorous use, so I need them handy, best: in a normal layout. When I use the character Bulgarian phonetic layout they show up as secondary characters, but there's no way of using them.

Before posting, I searched the forum and came up with a thread that suggested the use of a hotkeys-like software products, I've tried AutoKey and others, but they don't work, somehow. 

So that's what I need, a layout containing these two letters and/or a fast way to access them.

---

### Post by beren.olvar on 2010-07-14
I have done something similar to this, but for spanish layout in an english keyboard. Maybe we can accomplish this in the same way. There might be another, more standard way to do this, but you can try this if you like.

First you have to choose what combinations of keys you want to use for this letters. For example, in my keyboard I have an "AltGr" key which is pretty much useless, so I decided to use that key in combination with some other key to trigger the spanish characters, for example, in my ~/.Xmodmap file I have

```

keycode 108 = Mode_switch
keysym n = n N ntilde Ntilde

```

the syntax is simple, first you have to get the keycode of the modifier key using the xev application (run xev in a terminal and press the kay to see the output). In my case AltGr is keycode 108, and I assign to it the Mode_switch function. Next I am telling it to assign to the letter "n" in my keyboard the following values:

without moifier -> n
with Shift -> N
with Mode_switch -> ntilde (ñ)
with Shift+Mode_switch -> Ntilde (Ñ)

and there you go. So, what you have to do is to choose where to map those letters, and then find the "name" (ntilde in my case) for your letter. I couldn't find it on my computer, probably because of my choice of layout, so maybe you could post your /usr/include/X11/keysymdef.h file, so we can try to find the right name for your characters. Note that the file location may vary in your installation, so you may have to search for keysymdef.h if it's not there.

Edit: It would be useful if you could paste the contents of your keysymdef.h file and the output or this command:
xmodmap -pke -pm

---

### Post by simosx on 2010-07-14
> **tzarskielit said:**
> Hi guys, I need to access two Cyrillic letters which are now removed from the 'official' Bulgarian alphabet. 
[http://en.wikipedia.org/wiki/Yat](http://en.wikipedia.org/wiki/Yat) and [http://en.wikipedia.org/wiki/Little_Yus](http://en.wikipedia.org/wiki/Little_Yus)

It will be a vigorous use, so I need them handy, best: in a normal layout. When I use the character Bulgarian phonetic layout they show up as secondary characters, but there's no way of using them.

Before posting, I searched the forum and came up with a thread that suggested the use of a hotkeys-like software products, I've tried AutoKey and others, but they don't work, somehow. 

So that's what I need, a layout containing these two letters and/or a fast way to access them.

The characters you mention exist in the default Bulgarian keyboard layout,
/usr/share/X11/xkb/symbols/bg
Specifically, it's
[INDENT]  key <AC02> {   [ Cyrillic_ya,       Cyrillic_YA,
                   U0463,             U0462               ]    };
[/INDENT]

You access these with AltGr+ya and AltGr+YA.

Now, [http://en.wikipedia.org/wiki/Little_Yus](http://en.wikipedia.org/wiki/Little_Yus) mentions some characters that appear in Unicode 5.2 (Sept 2009). What you need to do is specify which Unicode characters (such as 'U0463') you want in the keyboard layout. Then, it's possible to find places in the Bulgarian layout, in a similar way with ya/YA, so that they are added. These changes can then be added to your local 'bg' file for use now, and at the same time request from the xkeyboard-config project to make those changes official for Ubuntu 10.10 and newer edition.

That's what we have done with the Greek layout, where we can type both modern and Ancient Greek with the default layout.

---

### Post by Zorgoth on 2010-07-14
I once set up a personal layout, which is much more complicated than what you are doing, but here it is:
```

partial default alphanumeric_keys
xkb_symbols "unicode" {

include "latin"

    name[Group1]="Poland";
    key <TLDE>  { [    dead_abovedot, U007E,      U0060,        U0060 ] };
    key <AE01>  { [     U0031,        U0021,      U21D2,        U21CF ] };
    key <AE02>  { [     U0032,        U0040,      U21D0,        U21CD ] };
    key <AE03>  { [     U0033,        U0023,      U21D4,        U21CE ] };
    key <AE04>  { [     U0034,        U0024,      U2208,        U2209 ] };
    key <AE05>  { [     U0035,        U0025,      U220B,        U220C ] };
    key <AE06>  { [     U0036,        U005E,      U22B2,        U22B4 ] };
    key <AE07>  { [     U0037,        U0026,      U22B3,        U22B5 ] };
    key <AE09>  { [     U0039,        U0028,      U2286,        U2288 ] };
    key <AE10>  { [     U0030,       U0029,      U2287,        U2289 ] };
    key <AE11>  { [     U002D,        U005F,      U2262,        U2263 ] };
    key <AE12>  { [     U003D,        U002B,      U2260,        U2295 ] };
    key <AD01>  { [         q,          Q,        U2203,        U2204 ] };
    key <AD02>  { [         w,          W,        U2200,        U2205 ] };
    key <AD03>	{ [         e,          E,      eogonek,      Eogonek ]	};
    key <AD04>  { [         r,          R,        U221A,        U224B ] };
    key <AD05>  { [         t,          T,        U2245,        U2247 ] };
    key <AD06>  { [         y,          Y,        U222B,        U222E ] };
    key <AD07>  { [         u,          U,        U222A,        U222A ] };
    key <AD08>  { [         i,          I,        U2229,        U221E ] };
    key <AD09>	{ [         o,          O,       oacute,       Oacute ]	};
    key <AD10>  { [         p,          P,        U00B1,        U2213 ] };
    key <AD11>  { [     U005B,      U007B,        U2282,        U2284 ] };
    key <AD12>  { [     U005D,      U007D,        U2283,        U2285 ] };
    key <BKSL>  { [     U005C,      U007C,        U2228,        U221F ] }; 
    key <AC01>	{ [         a,          A,      aogonek,      Aogonek ]	};
    key <AC02>	{ [         s,          S,       sacute,       Sacute ]	};
    key <AC03>  { [         d,          D,        U2202,        U2202 ] };
    key <AC04>  { [         f,          F,        U00A3,        U20AC ] };
    key <AC05>  { [         g,          G ] };
    key <AC06>  { [         h,          H ] };
    key <AC07>  { [         j,          J ] };
    key <AC08>  { [         k,          K ] };
    key <AC09>  { [         l,          L,        U0142,        U0141 ] };
    key <AC10>  { [     U003B,        U003A,      U227A,        U2280 ] };
    key <AC11>  { [     U0027,        U0022,      U227B,        U2281 ] };
    key <AB01>	{ [         z,          Z,    zabovedot,    Zabovedot ]	};
    key <AB02>	{ [         x,          X,       zacute,       Zacute ]	};
    key <AB03>	{ [         c,          C,       cacute,       Cacute ]	};
    key <AB04>  { [         v,          V,        U2206,        U2207 ] };
    key <AB05>  { [         b,          B ] };
    key <AB06>	{ [         n,          N,       nacute,       Nacute ]	};
    key <AB07>  { [         m,          M ] };
    key <AB08>  { [     U002C,      U003C,        U2264,        U226A ] };
    key <AB09>  { [     U002E,      U003E,        U2265,        U226B ] };
    key <AB10>  { [     U002F,      U003F,        U2227,        U221F ] };

    include "kpdl(comma)"
    include "level3(ralt_switch)"

};

```
(Sorry, forgot code tags first time)
Important things:
You will find the keyboard layouts in /usr/share/X11/xkb/symbols, at least on Ubuntu 10.04.
This is a Polish/mathematical keyboard, so not exactly what you want
xkb_symbols="unicode"
Perhaps include "latin" isn't what you want.
Uxxxx is just the unicode character with a particular hexadecimal code.


If you want right alt to switch your characters you need the
include "level3(ralt_switch)"

Some other useful things you can do more easily; for example to type Greek letters I use one of my Win keys; I don't do that by adding it to this layout, just by setting Greek as a secondary layout and setting Win key (while pressed) to change layout in keyboard layout prefrences.

---

### Post by simosx on 2010-07-14
```
xkb_symbols "unicode"
{
	name[Group1] = "Poland";
	include "latin(basic)"
	include "level3(ralt_switch)"
	include "kpdl(comma)"
	key <AB01> { [              z,              Z,      zabovedot,      Zabovedot ] }; // z Z &#380; &#379; 
	key <AB02> { [              x,              X,         zacute,         Zacute ] }; // x X &#378; &#377; 
	key <AB03> { [              c,              C,         cacute,         Cacute ] }; // c C &#263; &#262; 
	key <AB04> { [              v,              V,          U2206,          U2207 ] }; // v V &#8710; &#8711; 
	key <AB05> { [              b,              B                                 ] }; // b B 
	key <AB06> { [              n,              N,         nacute,         Nacute ] }; // n N &#324; &#323; 
	key <AB07> { [              m,              M                                 ] }; // m M 
	key <AB08> { [          U002C,          U003C,          U2264,          U226A ] }; // , < &#8804; &#8810; 
	key <AB09> { [          U002E,          U003E,          U2265,          U226B ] }; // . > &#8805; &#8811; 
	key <AB10> { [          U002F,          U003F,          U2227,          U221F ] }; // / ? &#8743; &#8735; 
	key <AC01> { [              a,              A,        aogonek,        Aogonek ] }; // a A &#261; &#260; 
	key <AC02> { [              s,              S,         sacute,         Sacute ] }; // s S &#347; &#346; 
	key <AC03> { [              d,              D,          U2202,          U2202 ] }; // d D &#8706; &#8706; 
	key <AC04> { [              f,              F,          U00A3,          U20AC ] }; // f F £ &#8364; 
	key <AC05> { [              g,              G                                 ] }; // g G 
	key <AC06> { [              h,              H                                 ] }; // h H 
	key <AC07> { [              j,              J                                 ] }; // j J 
	key <AC08> { [              k,              K                                 ] }; // k K 
	key <AC09> { [              l,              L,          U0142,          U0141 ] }; // l L &#322; &#321; 
	key <AC10> { [          U003B,          U003A,          U227A,          U2280 ] }; // ; : &#8826; &#8832; 
	key <AC11> { [          U0027,          U0022,          U227B,          U2281 ] }; // ' " &#8827; &#8833; 
	key <AD01> { [              q,              Q,          U2203,          U2204 ] }; // q Q &#8707; &#8708; 
	key <AD02> { [              w,              W,          U2200,          U2205 ] }; // w W &#8704; &#8709; 
	key <AD03> { [              e,              E,        eogonek,        Eogonek ] }; // e E &#281; &#280; 
	key <AD04> { [              r,              R,          U221A,          U224B ] }; // r R &#8730; &#8779; 
	key <AD05> { [              t,              T,          U2245,          U2247 ] }; // t T &#8773; &#8775; 
	key <AD06> { [              y,              Y,          U222B,          U222E ] }; // y Y &#8747; &#8750; 
	key <AD07> { [              u,              U,          U222A,          U222A ] }; // u U &#8746; &#8746; 
	key <AD08> { [              i,              I,          U2229,          U221E ] }; // i I &#8745; &#8734; 
	key <AD09> { [              o,              O,         oacute,         Oacute ] }; // o O ó Ó 
	key <AD10> { [              p,              P,          U00B1,          U2213 ] }; // p P ± &#8723; 
	key <AD11> { [          U005B,          U007B,          U2282,          U2284 ] }; // [ { &#8834; &#8836; 
	key <AD12> { [          U005D,          U007D,          U2283,          U2285 ] }; // ] } &#8835; &#8837; 
	key <AE01> { [          U0031,          U0021,          U21D2,          U21CF ] }; // 1 ! &#8658; &#8655; 
	key <AE02> { [          U0032,          U0040,          U21D0,          U21CD ] }; // 2 @ &#8656; &#8653; 
	key <AE03> { [          U0033,          U0023,          U21D4,          U21CE ] }; // 3 # &#8660; &#8654; 
	key <AE04> { [          U0034,          U0024,          U2208,          U2209 ] }; // 4 $ &#8712; &#8713; 
	key <AE05> { [          U0035,          U0025,          U220B,          U220C ] }; // 5 % &#8715; &#8716; 
	key <AE06> { [          U0036,          U005E,          U22B2,          U22B4 ] }; // 6 ^ &#8882; &#8884; 
	key <AE07> { [          U0037,          U0026,          U22B3,          U22B5 ] }; // 7 & &#8883; &#8885; 
	key <AE09> { [          U0039,          U0028,          U2286,          U2288 ] }; // 9 ( &#8838; &#8840; 
	key <AE10> { [          U0030,          U0029,          U2287,          U2289 ] }; // 0 ) &#8839; &#8841; 
	key <AE11> { [          U002D,          U005F,          U2262,          U2263 ] }; // - _ &#8802; &#8803; 
	key <AE12> { [          U003D,          U002B,          U2260,          U2295 ] }; // = + &#8800; &#8853; 
	key <BKSL> { [          U005C,          U007C,          U2228,          U221F ] }; // \ | &#8744; &#8735; 
	key <TLDE> { [  dead_abovedot,          U007E,          U0060,          U0060 ] }; // D&#729; ~ ` ` 
};

```

Thanks for the layout. I added a few comments for help.

---

### Post by tzarskielit on 2010-07-14
Thank you very much for your quick and concise help! My problem is solved. 
I hope that this thread will be helpful to others!:)

---

