---
title: "Bash Scripting help required to convert html to text"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by meindian523 on 2009-02-15
I have this(and 897 more) html file and I want to pull the word of the day which always starts on line 327(in all files) and ends on line 349(which is not constant in the files) from it.
```
<snip>

    <li><a href="/cgi-bin/wodcalendar.pl">Archive</a></li>
    <li><a href="/word/subscribe.htm">Sign Up</a></li>
    <li class="last"><a href="/word/subhelp.htm">Help</a></li>
</ul>
<div class="page_content_box">    
    <div class="wod_def">        
        <h1>The Word of the Day for April 01, 2007 is:</h1>
        <span class="headword">whammy</span>
        <span class="pronunc"> • \WAM-ee\ <a href="javascript:popWin('/cgi-bin/audio.pl?whammy01.wav=whammy')"><img src="/images/audio.gif" /></a> • </span>
        <span class="func">noun</span>        
        
        <dl>
            
            <dd><span class="sense_marker">1  a :</span> a supernatural power bringing bad luck</dd>
            
            <dd><span class="sense_marker">b  :</span> a magic curse or spell <strong>:</strong> jinx, hex</dd>
            
        </dl>
        
        <dl>
            
            <dd><span class="sense_marker">*2    :</span>  a potent force or attack; <em>specifically</em> <strong>:</strong> a paralyzing or lethal blow</dd>
            
        </dl>
        
        <h2>Example Sentence:</h2>
        <span class="verbal">&quot;The nation's working poor have been hit by another whammy,&quot; said the senator, referring to a recent tax hike.</span>
        <h2>Did you know?</h2>
        <span class="dyk">The origin of &quot;whammy&quot; is not entirely certain, but it is assumed to have been created by combining &quot;wham&quot; (&quot;a solid blow&quot;) with the whimsical &quot;-y&quot; ending. The first example of &quot;whammy&quot; in print occured in 1940, but the word was popularized in the 1950s by the cartoonist Al Capp in the comic strip &quot;Li'l Abner.&quot; The character Evil-Eye Fleegle could paralyze someone with the sheer power of his gaze. The &quot;single whammy&quot; was a look with one eye, and the fearsome &quot;double whammy&quot; used both eyes. As you may know, &quot;double whammy&quot; has also found a place in English as a general term. It means &quot;a combination of two adverse forces, circumstances, or effects&quot; -- in other words, a one-two punch. 
  
 <br /><br />*Indicates the sense illustrated by the example sentence.</span>
        <ul class="links">
            <li><a href="/word/index.xml"><img src="/images/feedpodcast.gif" /></a></li>
<snip>
```I thought of sed,but none of the options in man page seemed very useful.I tried lynx --dump,but even after redirection,it turned out to be a plain html file. :( Any body?

---

### Post by hossan on 2009-02-15
Hi,

You can use html2text for this,

install it using

*sudo apt-get install html2text*


And you can convert the html file to a text one by

[I]html2text input.html > output.txt
[/I]

---

### Post by meindian523 on 2009-02-15
```





                                            * Also Visit:
                                            * _U_n_a_b_r_i_d_g_e_d
                                            * _V_i_s_u_a_l
                                        _B_r_i_t_a_n_n_i_c_a_ _O_n_l_i_n_e_ _E_n_c_y_c_l_o_p_e_d_i_a
                                        ESL:
_[_G_o_ _t_o_ _h_o_m_e_p_a_g_e_._]                       _L_e_a_r_n_e_r_'_s_ _[_S_p_e_l_l_ _I_t_!_]
      _[_R_e_t_u_r_n_ _t_o_ _t_h_e_ _h_o_m_e_ _p_a_g_e_._]_H_o_m_e    for Kids:
      _[_E_x_p_a_n_d_/_c_o_l_l_a_p_s_e_ _m_e_n_u_._]_V_i_s_i_t_ _O_u_r  _W_o_r_d_ _C_e_n_t_r_a_l
      _S_i_t_e_s                             _S_p_e_l_l_ _I_t_!
      _U_n_a_b_r_i_d_g_e_d_ _D_i_c_t_i_o_n_a_r_y             #Dictionary oThesaurus oSpanish/English
      _L_e_a_r_n_e_r_'_s_ _D_i_c_t_i_o_n_a_r_y              oMedical [va                  ] [Submit
      _W_o_r_d_ _C_e_n_t_r_a_l_ _f_o_r_ _K_i_d_s             /images/search_button.gif]
      _C_o_l_l_e_g_i_a_t_e_ _D_i_c_t_i_o_n_a_r_y             Merriam-Webster PARTNERS
      _[_E_x_p_a_n_d_/_c_o_l_l_a_p_s_e_ _m_e_n_u_._]_P_r_e_m_i_u_m      _M_e_r_r_i_a_m_-_W_e_b_s_t_e_r_ _o_n_ _B_a_b_y_l_o_n_-_P_r_o
      _S_e_r_v_i_c_e_s                                Get instant results from Merriam-
      _U_n_a_b_r_i_d_g_e_d_ _D_i_c_t_i_o_n_a_r_y                   Webster in any desktop
      _C_o_l_l_e_g_i_a_t_e_ _D_i_c_t_i_o_n_a_r_y                   application in a single click!
      _E_n_c_y_c_l_o_p_e_d_i_a_ _B_r_i_t_a_n_n_i_c_a             _U_p_w_a_r_d_ _M_o_b_i_l_i_t_y_-_-_M_a_k_e_ _y_o_u_r_ _m_o_v_e_!
      _I_n_s_t_i_t_u_t_i_o_n_a_l_ _S_u_b_s_c_r_i_p_t_i_o_n_s             Classic Merriam-Webster content
      _[_E_x_p_a_n_d_/_c_o_l_l_a_p_s_e_ _m_e_n_u_._]_D_o_w_n_l_o_a_d_s        is now available on classic
      _G_o_o_g_l_e_ _G_a_d_g_e_t_s                          mobile platforms.
      _F_i_r_e_f_o_x_ _T_o_o_l_s                     _[_/_i_m_a_g_e_s_/_h_e_a_d_e_r_s_/
      _T_o_o_l_b_a_r                           _h_d_r___w_o_r_d___o_f___t_h_e___d_a_y_._g_i_f_]
      _S_i_d_e_b_a_r_ _T_a_b                           * _P_l_a_y_ _P_o_d_c_a_s_t
      _S_e_a_r_c_h_ _B_o_x_e_s                          * _A_r_c_h_i_v_e
      _[_E_x_p_a_n_d_/_c_o_l_l_a_p_s_e_ _m_e_n_u_._]_W_o_r_d_ _o_f        * _S_i_g_n_ _U_p
      _t_h_e_ _D_a_y                               * _H_e_l_p
      _T_o_d_a_y_'_s_ _W_o_r_d                      ************ TThhee WWoorrdd ooff tthhee DDaayy ffoorr AApprriill
      _A_r_c_h_i_v_e                           0011,, 22000077 iiss:: ************
      _S_u_b_s_c_r_i_b_e                         whammy  • \WAM-ee\ _[_/_i_m_a_g_e_s_/_a_u_d_i_o_._g_i_f_]
      _S_u_b_s_c_r_i_b_e_r_ _H_e_l_p                   •  noun
      _R_S_S_ _F_e_e_d                                1 a : a supernatural power
      _[_R_S_S_ _F_e_e_d_]                              bringing bad luck
      _[_E_x_p_a_n_d_/_c_o_l_l_a_p_s_e_ _m_e_n_u_._]_W_o_r_d_ _G_a_m_e_s       b : a magic curse or spell ::
      _T_o_d_a_y_'_s_ _G_a_m_e                            jinx, hex
      _M_o_r_e_ _W_o_r_d_ _G_a_m_e_s                         *2 : a potent force or attack;
      _D_a_i_l_y_ _C_r_o_s_s_w_o_r_d_s                        ssppeecciiffiiccaallllyy :: a paralyzing or
      _S_C_R_A_B_B_L_E                                lethal blow
      _[_E_x_p_a_n_d_/_c_o_l_l_a_p_s_e_ _m_e_n_u_._]_O_p_e_n       ********** EExxaammppllee SSeenntteennccee:: **********
      _D_i_c_t_i_o_n_a_r_y                        "The nation's working poor have been
      _L_a_t_e_s_t_ _E_n_t_r_i_e_s                    hit by another whammy," said the
      _A_l_p_h_a_b_e_t_i_c_a_l_ _B_r_o_w_s_e               senator, referring to a recent tax
      _B_r_o_w_s_e_ _C_a_t_e_g_o_r_i_e_s                 hike.
      _S_u_b_m_i_t_ _a_n_ _E_n_t_r_y                   ********** DDiidd yyoouu kknnooww?? **********
      _[_E_x_p_a_n_d_/_c_o_l_l_a_p_s_e_ _m_e_n_u_._]_S_p_e_l_l_i_n_g   The origin of "whammy" is not entirely
      _B_e_e_ _H_i_v_e                          certain, but it is assumed to have been
      _H_i_v_e_ _H_e_a_d_q_u_a_r_t_e_r_s                 created by combining "wham" ("a solid
      _S_p_e_l_l_i_n_g_ _C_h_a_m_p_i_o_n                 blow") with the whimsical "-y" ending.
      _S_p_e_l_l_i_n_g_ _Q_u_i_z                     The first example of "whammy" in print
      _S_p_e_l_l_i_n_g_ _R_e_f_o_r_m                   occured in 1940, but the word was
      _P_r_i_z_e_s                            popularized in the 1950s by the
      _W_i_n_n_i_n_g_ _W_o_r_d_s                     cartoonist Al Capp in the comic strip
      _W_o_r_d_ _P_a_n_e_l_i_s_t_s                    "Li'l Abner." The character Evil-Eye
      _[_E_x_p_a_n_d_/_c_o_l_l_a_p_s_e_ _m_e_n_u_._]_W_o_r_d_ _f_o_r   Fleegle could paralyze someone with the
      _t_h_e_ _W_i_s_e                          sheer power of his gaze. The "single
      _T_o_d_a_y_'_s_ _B_r_o_a_d_c_a_s_t                 whammy" was a look with one eye, and
      _A_r_c_h_i_v_e                           the fearsome "double whammy" used both
      _A_b_o_u_t_ _W_F_T_W                        eyes. As you may know, "double whammy"
      _[_E_x_p_a_n_d_/_c_o_l_l_a_p_s_e_ _m_e_n_u_._]_O_n_l_i_n_e     has also found a place in English as a
      _S_t_o_r_e                             general term. It means "a combination
      _B_o_o_k_s_ _a_n_d_ _C_D_-_R_o_m_s                 of two adverse forces, circumstances,
      _O_n_l_i_n_e_ _S_e_r_v_i_c_e_s                   or effects" -- in other words, a one-
      _H_a_n_d_h_e_l_d_s                         two punch.
      _P_a_l_m_ _a_n_d_ _P_o_c_k_e_t_ _P_C
      _W_i_r_e_l_e_s_s                          *Indicates the sense illustrated by the
      _[_E_x_p_a_n_d_/_c_o_l_l_a_p_s_e_ _m_e_n_u_._]_H_e_l_p       example sentence.
      _L_o_o_k_i_n_g_ _U_p_ _a_ _W_o_r_d                     * _[_/_i_m_a_g_e_s_/_f_e_e_d_p_o_d_c_a_s_t_._g_i_f_]
      _F_A_Q                                   * _W_h_a_t_'_s_ _t_h_i_s_?
      _C_i_t_i_n_g_ _t_h_e_ _D_i_c_t_i_o_n_a_r_y                 * _P_l_a_y_ _t_o_d_a_y_'_s_ _p_o_d_c_a_s_t
      _A_u_d_i_o_ _P_r_o_n_u_n_c_i_a_t_i_o_n_s                  * Theme music by Joshua Stamper
      _W_o_r_d_ _G_a_m_e_s_ _H_e_l_p                         ©2006 _N_e_w_ _J_e_r_u_s_a_l_e_m_ _M_u_s_i_c_/_A_S_C_A_P
      _T_o_o_l_b_a_r_ _H_e_l_p
      _C_D_-_R_O_M_ _S_u_p_p_o_r_t                    Share this entry:    _[_S_h_a_r_e_ _t_h_i_s_ _w_o_r_d
      _[_E_x_p_a_n_d_/_c_o_l_l_a_p_s_e_ _m_e_n_u_._]_A_b_o_u_t_ _U_s   _w_i_t_h_ _d_i_g_g_] _[_S_h_a_r_e_ _t_h_i_s_ _w_o_r_d_ _w_i_t_h
      _M_e_r_r_i_a_m_-_W_e_b_s_t_e_r_ _F_A_Q               _r_e_d_d_i_t_] _[_S_h_a_r_e_ _t_h_i_s_ _w_o_r_d_ _w_i_t_h
      _P_r_e_s_s_ _R_e_l_e_a_s_e_s                    _t_e_c_h_n_o_r_a_t_i_] _[_S_h_a_r_e_ _t_h_i_s_ _w_o_r_d_ _w_i_t_h
      _A_d_v_e_r_t_i_s_i_n_g_ _I_n_f_o                  _d_e_l_._i_c_i_o_._u_s_] _[_S_h_a_r_e_ _t_h_i_s_ _w_o_r_d_ _w_i_t_h
      _R_e_t_a_i_l_e_r_s                         _f_u_r_l_] _[_S_h_a_r_e_ _t_h_i_s_ _w_o_r_d_ _w_i_t_h
      _C_o_n_t_a_c_t_ _U_s                        _s_t_u_m_b_l_e_u_p_o_n_] _[_S_h_a_r_e_ _t_h_i_s_ _w_o_r_d_ _w_i_t_h
      _P_r_i_v_a_c_y_ _P_o_l_i_c_y                    _g_o_o_g_l_e_] _[_S_h_a_r_e_ _t_h_i_s_ _w_o_r_d_ _w_i_t_h
      _C_o_p_y_r_i_g_h_t_ _N_o_t_i_c_e                  _b_l_i_n_k_l_i_s_t_] _[_S_h_a_r_e_ _t_h_i_s_ _w_o_r_d_ _w_i_t_h
                                        _n_e_w_s_v_i_n_e_] _[_S_h_a_r_e_ _t_h_i_s_ _w_o_r_d_ _w_i_t_h
                                        _f_a_c_e_b_o_o_k_] _[_S_h_a_r_e_ _t_h_i_s_ _w_o_r_d_ _w_i_t_h
                                        _m_y_s_p_a_c_e_]

                                        Link to this page:   
                                        [Unknown INPUT type]
    * _P_r_o_d_u_c_t_s
    * _P_r_e_m_i_u_m_ _S_e_r_v_i_c_e_s
    * _C_o_m_p_a_n_y_ _I_n_f_o
    * _C_o_n_t_a_c_t_ _U_s
    * _A_d_v_e_r_t_i_s_i_n_g_ _I_n_f_o
    * _P_r_i_v_a_c_y_ _P_o_l_i_c_y
_©
 Merriam-Webster, Incorporated

  [Quantcast]
```
Not much helpful :(

---

### Post by meindian523 on 2009-02-15
And on my Gedit,all the A_B_ etc are nice boxes.

---

### Post by hossan on 2009-02-15
Can you try this one , for me it worked flawlessly 


html2text -o test.text test.html

========================

Archive
Sign Up
Help
****** The Word of the Day for April 01, 2007 is: ******
whammy  • \WAM-ee\ [/images/audio.gif] •  noun
      1 a : a supernatural power bringing bad luck
      b : a magic curse or spell : jinx, hex
      *2 : a potent force or attack; specifically : a paralyzing or lethal blow
***** Example Sentence: *****
"The nation's working poor have been hit by another whammy," said the senator,
referring to a recent tax hike.
***** Did you know? *****
The origin of "whammy" is not entirely certain, but it is assumed to have been
created by combining "wham" ("a solid blow") with the whimsical "-y" ending.
The first example of "whammy" in print occured in 1940, but the word was
popularized in the 1950s by the cartoonist Al Capp in the comic strip "Li'l
Abner." The character Evil-Eye Fleegle could paralyze someone with the sheer
power of his gaze. The "single whammy" was a look with one eye, and the
fearsome "double whammy" used both eyes. As you may know, "double whammy" has
also found a place in English as a general term. It means "a combination of two
adverse forces, circumstances, or effects" -- in other words, a one-two punch.

*Indicates the sense illustrated by the example sentence.
    * [/images/feedpodcast.gif]
    *

========================

---

### Post by Xiong Chiamiov on 2009-02-15
> **meindian523 said:**
> I want to do text processing on a bunch of files.
Perl.

---

### Post by meindian523 on 2009-02-15
Looks like I'm missing something,because the same thing and all the boxes again,the ones which appear when the character is not recognised.

---

### Post by meindian523 on 2009-02-15
Xiong,probably,if I knew Perl.And single word answers,unless they are commands to be entered,hardly help.

---

### Post by Xiong Chiamiov on 2009-02-15
> **meindian523 said:**
> Xiong,probably,if I knew Perl.And single word answers,unless they are commands to be entered,hardly help.
I had a fairly similar situation this summer.  I realized that Perl was the best thing for the job, so I spent an hour or two learning enough to write up a script to do the job.  Yes, it was a fairly inelegant solution, but it was a fairly low investment of time, considering the return.

In this case, the best way would probably be to [read the entire file into a string](http://www.google.com/search?hl=en&q=perl%20read%20entire%20file%20into%20string&aq=f&oq=), then use a regex to capture it, since you know what will always be before and after it.

As someone's sig in the Arch Linux forums say, it's easier to learn Perl than awk and sed.  You'll doubtless use it later on, so you might as well learn it now.

Also, don't double-post; use the edit button.

---

### Post by meindian523 on 2009-02-15
ah,that was unintentional.

---

### Post by meindian523 on 2009-02-19
Well,I tried the link you pointed to,but none of it made any sense to me,being a newbie to Perl.So,bump.

---

### Post by meindian523 on 2009-02-19
bump.The way hossan pointed out works,but I'm unable to read the output,what am I missing?I'm using Ubuntu 8.10 64 bit.

---

### Post by insineratehymn on 2009-02-19
I don't know if there is going to be an out of the box utility that you are looking for. As someone said earlier... text processing... a bunch... perl.

There are **lots** of perl support forums and **lots** of documentation for it. It isn't hard to learn either, you have linux already. It **will** help you and you will love it, I promise.

---

### Post by adam_kimber on 2009-02-19
When you get rectangles it usually means that you are missing a font. However it could also mean that the character encoding is wierd. Copy of paste the text from your first post to gedit, save the file and then run the way hossan suggests. That should produce a readable output. 

I think the html encoding tag at the top might be messing with the output. Try removing that and running the result.

---

### Post by meindian523 on 2009-02-19
There's an improvement,but not by much.
```
_A_r_c_h_i_v_e
_S_i_g_n_ _U_p
_H_e_l_p
************ TThhee WWoorrdd ooff tthhee DDaayy ffoorr AApprriill 0011,, 22000077 iiss:: ************
whammy  &#8226; \WAM-ee\ _[_/_i_m_a_g_e_s_/_a_u_d_i_o_._g_i_f_] &#8226;  noun
      1 a : a supernatural power bringing bad luck
      b : a magic curse or spell :: jinx, hex
      *2 : a potent force or attack; ssppeecciiffiiccaallllyy :: a paralyzing or lethal blow
********** EExxaammppllee SSeenntteennccee:: **********
"The nation's working poor have been hit by another whammy," said the senator,
referring to a recent tax hike.
********** DDiidd yyoouu kknnooww?? **********
The origin of "whammy" is not entirely certain, but it is assumed to have been
created by combining "wham" ("a solid blow") with the whimsical "-y" ending.
The first example of "whammy" in print occured in 1940, but the word was
popularized in the 1950s by the cartoonist Al Capp in the comic strip "Li'l
Abner." The character Evil-Eye Fleegle could paralyze someone with the sheer
power of his gaze. The "single whammy" was a look with one eye, and the
fearsome "double whammy" used both eyes. As you may know, "double whammy" has
also found a place in English as a general term. It means "a combination of two
adverse forces, circumstances, or effects" -- in other words, a one-two punch.

*Indicates the sense illustrated by the example sentence.
    * _[_/_i_m_a_g_e_s_/_f_e_e_d_p_o_d_c_a_s_t_._g_i_f_]
    *
```

---

### Post by adam_kimber on 2009-02-19
Hi tried it on my machine and command line output works fine. But if you try to pipe it to a text file either through the internal command or via bash scripting you get the weird characters. To solve this you need the following switch ```
-nobs
```

To make a nice ouput run the following code. 

```
html2text -style pretty -nobs -o test.txt test.html
```

Where test.txt is your output and test,html is your input. Now you have a working command line you can get Bash to work on multiple files using this. I know it is possible but I cannot think immediately how to do it. You need to have two variables input and output and a for loop but that is as far as I can get at the moment. 

I have attached my output of the html from your original post using the above command.

---

### Post by meindian523 on 2009-02-20
@adam_kimber
Ok,that worked,now I just wish it would work on the source file. :(
When I use the source file,I get a blank text file.

---

### Post by adam_kimber on 2009-02-20
Got the source file so I can have a play?

---

### Post by meindian523 on 2009-02-21
Karmic Koala,no Kinetic Kiwi.The source file
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <meta name="Description" content="Merriam-Webster provides a free online dictionary, thesaurus, audio pronunciations, Word of the Day, word games, and other English language resources." />
        <meta name="Keywords" content="merriam-webster, dictionary, online dictionary, webster's dictionary, talking dictionary, english language, online thesaurus, word of the day, word games, word for the wise" />
        <meta name="robots" content="Index, follow" />
        <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
        <title>Merriam-Webster Online</title>
        <link rel="icon" href="/favicon.ico" type="image/x-icon" />        
        <link href="/css/global.css" rel="stylesheet" type="text/css" />
        <link href="/css/inner.css" rel="stylesheet" type="text/css" />
        
        <script type="text/javascript" src="/js/googleads.js"></script>        
        <script type="text/javascript" src="/js/menus.js"></script>
        <script type="text/javascript" src="/js/word_of_the_day_box.js"></script>
        <script type="text/javascript" src="/js/open_dictionary_box.js"></script>
        <script type="text/javascript" src="/js/global.js"></script>    
        <script type="text/javascript" src="/js/temp/accipiter.js"></script>    
        <script type="text/javascript">
            <!--                
                
                // This function initialize the page.
                function initAccipiterPage ()
                    {    // Initialize the page as usual.
                        initPageInner();

                        // The page id.
                        var page_id = "word";

                        // Get the creative area.
                        var area = "GEN";

                        if ( page_id == "game" )
                            {    area    = "GAMES";
                                var loc    = document.location.href + "";

                                if ( loc.indexOf("_play.htm") >= 0 )
                                    {    area = "GAMES2";
                                    }; // if ( loc.indexOf("_play.htm") >= 0 )
                            }
                            
                        else if ( page_id == "word" )
                            {    area = "WOD";
                            }; 

                        // Set the area and keyword to pass along to accipiter.
                        setGlobalCreativeData(area, "");

                        // Load the creatives.
                        loadCreatives();
                    }; // function initAccipiterPage ()

            // -->
        </script>
    </head>
    <body class="page &page.page_id;" onload="initAccipiterPage()">
        <div id="page_wrapper">
            <table border="0" cellpadding="0" cellspacing="0" id="content">
                <tr>
                    <td class="left_col">
                        <div class="logo"><a href="/"><img src="/images/hdr_mw_logo_area.gif" alt="Go to homepage." /></a></div>
                        <dl id="nav_menu" class="nav_menu">
                            <dd id="menu_home"><a href="/"><img src="/images/button.gif" alt="Return to the home page." /></a><a href="/">Home</a></dd>
                            <dd id="menu_visit"><a href="#" onclick="return show_submenu('nav_menu', 'visit_');"><img src="/images/button.gif" alt="Expand/collapse menu." /></a><a href="#" onclick="return show_submenu('nav_menu', 'visit_');">Visit Our Sites</a></dd>
                            <dd id="visit_unabridged" class="submenu"><a href="http://unabridged.merriam-webster.com/?refr=U_mwol_nav">Unabridged Dictionary</a></dd>
                            <dd id="visit_learners" class="submenu"><a href="http://www.learnersdictionary.com/">Learner's Dictionary</a></dd>
                            <dd id="visit_word_central" class="submenu"><a href="http://www.wordcentral.com/">Word Central for Kids</a></dd>
                            <dd id="visit_collegiate" class="submenu"><a href="http://www.merriam-webstercollegiate.com/?refr=C_mwol_nav">Collegiate Dictionary</a></dd>
                            
                            <dd id="menu_ps"><a href="#" onclick="return show_submenu('nav_menu', 'ps_');"><img src="/images/button.gif" alt="Expand/collapse menu." /></a><a href="#" onclick="return show_submenu('nav_menu', 'ps_');">Premium Services</a></dd>
                            <dd id="ps_unabridged" class="submenu"><a href="http://unabridged.merriam-webster.com/?refr=U_mwol_nav">Unabridged Dictionary</a></dd>
                            <dd id="ps_collegiate" class="submenu"><a href="http://www.merriam-webstercollegiate.com/?refr=C_mwol_nav">Collegiate Dictionary</a></dd>
                            <dd id="ps_britannica" class="submenu"><a href="http://www.britannica.com">Encyclopedia Britannica</a></dd>
                            <dd id="ps_muser_licenses" class="submenu"><a href="/premium/institutions.html">Institutional Subscriptions</a></dd>
                            
                            <dd id="menu_downloads"><a href="#" onclick="return show_submenu('nav_menu', 'downloads_');"><img src="/images/button.gif" alt="Expand/collapse menu." /></a><a href="/downloads/index.htm">Downloads</a></dd>
                            <dd id="downloads_google_gadgets" class="submenu"><a href="/downloads/index.htm?downloads_google">Google Gadgets</a></dd>
                            <dd id="downloads_firefox_tools" class="submenu"><a href="/downloads/index.htm?downloads_firefox">Firefox Tools</a></dd>
                            <dd id="downloads_toolbar" class="submenu"><a href="/downloads/general/toolbar_ie.htm">Toolbar</a></dd>
                            <dd id="downloads_sidebar_tab" class="submenu"><a href="/downloads/general/sidebar_tab_netscape.htm">Sidebar Tab</a></dd>
                            <dd id="downloads_search_boxes" class="submenu"><a href="/downloads/general/search_box.htm">Search Boxes</a></dd>
                            
                            <dd id="menu_word" class="expanded"><a href="#" onclick="return show_submenu('nav_menu', 'word_');"><img src="/images/button.gif" alt="Expand/collapse menu." /></a><a href="/cgi-bin/mwwod.pl">Word of the Day</a></dd>
                            <dd id="word_todays_word" class="submenu" style="display: block;"><a href="/cgi-bin/mwwod.pl">Today's Word</a></dd>
                            <dd id="word_archive" class="submenu" style="display: block;"><a href="/cgi-bin/wodcalendar.pl">Archive</a></dd>
                            <dd id="word_subscribe" class="submenu" style="display: block;"><a href="/word/subscribe.htm">Subscribe</a></dd>
                            <dd id="word_help" class="submenu" style="display: block;"><a href="/word/subhelp.htm">Subscriber Help</a></dd>
                            <dd id="word_rss_feed" class="submenu" style="display: block;"><a href="/word/index.xml">RSS Feed</a></dd>
                            <dd id="word_pod_cast" class="submenu" style="display: block;"><a href="/word/index.xml"><img src="/images/feedpodcast.gif" alt="RSS Feed" /></a></dd>
                            
                            <dd id="menu_game"><a href="#" onclick="return show_submenu('nav_menu', 'game_');"><img src="/images/button.gif" alt="Expand/collapse menu." /></a><a href="/game/index.htm">Word Games</a></dd>
                            <dd id="game_todays_game" class="submenu"><a href="/game/index.htm">Today's Game</a></dd>
                            <dd id="game_more_games" class="submenu"><a href="/game/more.htm">More Word Games</a></dd>
                            <dd id="game_daily_crossword" class="submenu"><a href="/game/crossword.htm">Daily Crosswords</a></dd>
                            <dd id="game_scrabble" class="submenu_red"><a href="/game/scrabble.htm">SCRABBLE</a></dd>
                            
                            <dd id="menu_open_dict"><a href="#" onclick="return show_submenu('nav_menu', 'open_dict');"><img src="/images/button.gif" alt="Expand/collapse menu." /></a><a href="http://www3.merriam-webster.com/opendictionary/">Open Dictionary</a></dd>
                            <dd id="open_dict_browse_recent" class="submenu"><a href="http://www3.merriam-webster.com/opendictionary/newword_display_recent.php">Latest Entries</a></dd>
                            <dd id="open_dict_browse_alpha" class="submenu"><a href="http://www3.merriam-webster.com/opendictionary/newword_display_alpha.php">Alphabetical Browse</a></dd>
                            <dd id="open_dict_browse_cat" class="submenu"><a href="http://www3.merriam-webster.com/opendictionary/newword_display_cat.php">Browse Categories</a></dd>
                            <dd id="open_dict_submit_entry" class="submenu"><a href="http://www3.merriam-webster.com/opendictionary/guide.php">Submit an Entry</a></dd>
                            
                            <dd id="menu_spell"><a href="#" onclick="return show_submenu('nav_menu', 'spell_');"><img src="/images/button.gif" alt="Expand/collapse menu." /></a><a href="/spell/index.htm">Spelling Bee Hive</a></dd>
                            <dd id="spell_headquarters" class="submenu"><a href="/spell/hivehq.htm">Hive Headquarters</a></dd>
                            <dd id="spell_champion" class="submenu"><a href="/spell/winner.htm">Spelling Champion</a></dd>
                            <dd id="spell_quiz" class="submenu"><a href="/cgi-bin/spquiz.pl">Spelling Quiz</a></dd>
                            <dd id="spell_reform" class="submenu"><a href="/info/spelling-reform.htm">Spelling Reform</a></dd>
                            <dd id="spell_prizes" class="submenu"><a href="/spell/prizes.htm">Prizes</a></dd>
                            <dd id="spell_winning_words" class="submenu"><a href="/spell/words.htm">Winning Words</a></dd>
                            <dd id="spell_panelists" class="submenu"><a href="/spell/panelists.htm">Word Panelists</a></dd>
                            
                            <dd id="menu_wftw"><a href="#" onclick="return show_submenu('nav_menu', 'wftw_');"><img src="/images/button.gif" alt="Expand/collapse menu." /></a><a href="/cgi-bin/wftw.pl">Word for the Wise</a></dd>
                            <dd id="wftw_todays_broadcast" class="submenu"><a href="/cgi-bin/wftw.pl">Today's Broadcast</a></dd>
                            <dd id="wftw_archive" class="submenu"><a href="/cgi-bin/wftw_arcindex.pl">Archive</a></dd>
                            <dd id="wftw_about" class="submenu"><a href="/wftw/about.htm">About WFTW</a></dd>
                            
                            <dd id="menu_store"><a href="#" onclick="return show_submenu('nav_menu', 'store_');"><img src="/images/button.gif" alt="Expand/collapse menu." /></a><a href="/store/index.htm">Online Store</a></dd>
                            <dd id="store_books_cds" class="submenu"><a href="/store/books_and_cds.htm">Books and CD-Roms</a></dd>
                            <dd id="store_services" class="submenu"><a href="/cgi-bin/unabridged_sub.pl?refr=P_mwol_nav_store">Online Services</a></dd>
                            <dd id="store_handhelds" class="submenu"><a href="/store/handhelds.htm">Handhelds</a></dd>
                            <dd id="store_palm_pck_pc" class="submenu"><a href="/store/palm.htm">Palm and Pocket PC</a></dd>
                            <dd id="store_wireless" class="submenu"><a href="/store/wireless.htm">Wireless</a></dd>
                            
                            <dd id="menu_help"><a href="#" onclick="return show_submenu('nav_menu', 'help_');"><img src="/images/button.gif" alt="Expand/collapse menu." /></a><a href="/help/index.htm">Help</a></dd>
                            <dd id="help_word_lookup" class="submenu"><a href="/help/searching.htm">Looking Up a Word</a></dd>
                            <dd id="help_faq" class="submenu"><a href="/help/faq.htm">FAQ</a></dd>
                            <dd id="help_citing_dict" class="submenu"><a href="/help/citing.htm">Citing the Dictionary</a></dd>
                            <dd id="help_audio_pron" class="submenu"><a href="/help/audiofaq.htm">Audio Pronunciations</a></dd>
                            <dd id="help_word_games" class="submenu"><a href="/help/game/help.htm">Word Games Help</a></dd>
                            <dd id="help_toolbar" class="submenu"><a href="/help/toolbar/help.htm">Toolbar Help</a></dd>
                            <dd id="help_cdrom_support" class="submenu"><a href="/help/support.htm">CD-ROM Support</a></dd>
                            
                            <dd id="menu_info"><a href="#" onclick="return show_submenu('nav_menu', 'info_');"><img src="/images/button.gif" alt="Expand/collapse menu." /></a><a href="/info/index.htm">About Us</a></dd>
                            <dd id="info_faq" class="submenu"><a href="/info/faq.htm">Merriam-Webster FAQ</a></dd>
                            <dd id="info_press" class="submenu"><a href="/info/press.htm">Press Releases</a></dd>
                            <dd id="info_ads" class="submenu"><a href="/info/advertising.htm">Advertising Info</a></dd>
                            <dd id="info_retailers" class="submenu"><a href="/info/retailers.htm">Retailers</a></dd>
                            <dd id="info_contact" class="submenu"><a href="/info/contact.htm">Contact Us</a></dd>
                            <dd id="info_privacy" class="submenu"><a href="/info/privacy.htm">Privacy Policy</a></dd>
                            <dd id="info_copyright" class="submenu"><a href="/info/copyright.htm">Copyright Notice</a></dd>
                        </dl>
                    </td>
                    <td class="right_col">
                        <div class="banner_ad">
                             <div id="google_creative_2">
                                <script type="text/javascript">
                                    <!-- 
                                        placeCreative("google_creative_2", "BANNER", "tb", "");
                                    // -->
                                </script>
                             </div>
                        </div>
                        <div class="hnav_bar">
                            <ul>
                                <li class="section">Also Visit:</li>
                                <li><a href="http://unabridged.merriam-webster.com/?refr=U_mwol_top">Unabridged</a></li>
                                <li><a href="http://visual.merriam-webster.com/">Visual</a></li>
                                <script type="text/javascript">
                                if ( !isScreen800x600() )
                                    { document.write('<li><a href="http://www.britannica.com">Britannica Online Encyclopedia</a></li>');
                                    };
                                </script>
                                <noscript><li class="last"><a href="http://www.britannica.com">Britannica Online Encyclopedia</a></li></noscript>
                                <li class="section">ESL:</li>
                                <li class="last"><a href="http://www.learnersdictionary.com/">Learner's <img src="/images/new2.gif" alt="Spell It!" /></a></li>
                                  <li class="section">for Kids:</li>
                                <li><a href="http://www.wordcentral.com">Word Central</a></li>
                                <li class="last"><a href="http://www.myspellit.com/">Spell It!</a></li>
                          </ul>
                            <div style="clear: both;"></div>
                        </div>
                        <div class="search_bar">
                            <form id="search_form" action="/dictionary" method="get" onsubmit="return lookup('search_form');">
                                <div>
                                    <input id="source_dict" name="book" type="radio" value="dictionary" checked="checked" /><label for="source_dict">Dictionary</label>
                                    <input id="source_thes" name="book" type="radio" value="thesaurus" /><label for="source_thes">Thesaurus</label>
                                    <input id="source_spanish" name="book" type="radio" value="spanish_english" /><label for="source_spanish">Spanish/English</label>
                                    <input id="source_medical" name="book" type="radio" value="medical" /><label for="source_spanish">Medical</label>
                                    <input id="search_box_terms" name="va" type="text" class="text_field" value="" maxlength="50" />
                                    <input type="image" class="search_button" src="/images/search_button.gif" />
                                </div>
                            </form>
                        </div>
                        <div style="clear: both; float: none;"></div>
                        <div class="ad_space">
                            <div class="tool_box misc">
                                <div class="title">Merriam-Webster PARTNERS</div>
                                <div class="content">
                                    <dl>
                                        <dt><a href="http://affiliates.babylon.com/z/54/CD1">Merriam-Webster on Babylon-Pro</a></dt>
                                        <dd><img src="/images/partners_graphic_wod_pg.gif" style="float: right;" alt="" />Get instant results from Merriam-Webster in any desktop application in a single click!</dd>
                                        <dt><a href="http://www.mobile-webster.com/?source=MWOL">Upward Mobility--Make your move!</a></dt>
                                        <dd>
                                            Classic Merriam-Webster content is now available on classic mobile platforms.
                                        </dd>
                                    </dl>                                        
                                </div>
                            </div>
                            <div id="main_ad">
<script type="text/javascript">
    <!--
        // The adaptvAdPlayer object doesn't exist or the hasCompanionAd method is not present; therefore, 
        // display the default ad.
        if ( typeof(adaptvAdPlayer) == "undefined" || typeof(adaptvAdPlayer.hasCompanionAd) == "undefined" )
            {    placeCreative("main_ad", "300x250", "rec1", "");
            } // else if ( typeof(adaptvAdPlayer) == "undefined" || typeof(adaptvAdPlayer.hasCompanionAd) == "undefined" )

        // Adaptv doesn't have a companion ad; therefore, display the default advertisement.
        else if ( !adaptvAdPlayer.hasCompanionAd() ) 
            {    placeCreative("main_ad", "300x250", "rec1", "");
            }; // if ( !adaptvAdPlayer.hasCompanionAd() ) 
    // -->
</script>
                            </div>
                            <div style="padding-top: 5px;">
                                <link href="/css/ebgamespromo.css" rel="stylesheet" type="text/css" />
                                <script type="text/javascript" src="/js/gamespromo.js"></script>
                            </div>
                        </div>
                        <div class="page_content">
                            <style type="text/css">
div.wod_def
{    font: normal 10pt Arial, Verdana, Sans-Serif;
}
div.wod_def dl
{    display: block;
    margin: 5px 0 5px 0;
    padding: 0;
}
div.wod_def dl dd
{    display: inline;
    margin: 0;
    padding: 0;
}
div.wod_def dl dd span.sense_marker
{    font-weight: bold;
}
div.wod_def dl dd span.sense_marker em
{    font-weight: normal;
}
div.wod_def dl dt
{    display: none;
}
div.wod_def h1
{    color: #000066;
    font-size: 1.2em;
    font-weight: bold;
    margin: 5px 0 5px 0;
    padding: 0;
}
div.wod_def h2
{    color: #000066;
    font-size: 1em;
    font-weight: bold;
    margin: 10px 0 0 0;
    padding: 0;
}
div.wod_def span.headword
{    font-weight: bold;
}
div.wod_def img
{    border: 0;
    margin: 0;
    padding: 0;
}
div.wod_def ul.credits
{    margin: 10px 0 5px 0;
    padding: 0;
}
div.wod_def ul.credits li
{    display: inline;
    font-size: .85em;
    list-style: none;
    margin: 0;
    padding: 0 10px 0 0;
}
div.wod_def ul.credits li a, div.wod_def ul.credits li a:hover, div.wod_def ul.credits li a:link, div.wod_def ul.credits li a:visited
{    color: #712794;
    font-size: .85em;    
    font-weight: bold;
}
div.wod_def ul.footnotes
{    margin: 15px 0 5px 0;
    padding: 0;
}
div.wod_def ul.footnotes li
{    font-size: .85em;
    list-style: none;
    margin: 0;
    padding: 0;
}
div.wod_def ul.links
{    margin: 10px 0 5px 0;
    padding: 0;
}
div.wod_def ul.links li
{    display: inline;
    font-size: .85em;
    list-style: none;
    margin: 0;
    padding: 0 10px 0 0;
}
div.wod_def ul.links li a, div.wod_def ul.links li a:hover, div.wod_def ul.links li a:link, div.wod_def ul.links li a:visited
{    color: #712794;
    font-size: .85em;
    font-weight: bold;
}
</style>
<script type="text/javascript">
<!--
    function rssWin()
        {    aWindow=window.open("/word/rss.html","rss_window","toolbar=no,status=yes,resizable=yes,menubar=no,width=430,height=490");
        };

    var wodToken = "whammy";
-->
</script>
<div><a href="/cgi-bin/mwwod.pl"><img src="/images/headers/hdr_word_of_the_day.gif" /></a></div>
<ul class="page_links">
    <li><a href="http://condor.eb.com/word/podcast/wd20070401.mp3">Play Podcast</a></li>
    <li><a href="/cgi-bin/wodcalendar.pl">Archive</a></li>
    <li><a href="/word/subscribe.htm">Sign Up</a></li>
    <li class="last"><a href="/word/subhelp.htm">Help</a></li>
</ul>
<div class="page_content_box">    
    <div class="wod_def">        
        <h1>The Word of the Day for April 01, 2007 is:</h1>
        <span class="headword">whammy</span>
        <span class="pronunc"> &#8226; \WAM-ee\ <a href="javascript:popWin('/cgi-bin/audio.pl?whammy01.wav=whammy')"><img src="/images/audio.gif" /></a> &#8226; </span>
        <span class="func">noun</span>        
        
        <dl>
            
            <dd><span class="sense_marker">1  a :</span> a supernatural power bringing bad luck</dd>
            
            <dd><span class="sense_marker">b  :</span> a magic curse or spell <strong>:</strong> jinx, hex</dd>
            
        </dl>
        
        <dl>
            
            <dd><span class="sense_marker">*2    :</span>  a potent force or attack; <em>specifically</em> <strong>:</strong> a paralyzing or lethal blow</dd>
            
        </dl>
        
        <h2>Example Sentence:</h2>
        <span class="verbal">&quot;The nation's working poor have been hit by another whammy,&quot; said the senator, referring to a recent tax hike.</span>
        <h2>Did you know?</h2>
        <span class="dyk">The origin of &quot;whammy&quot; is not entirely certain, but it is assumed to have been created by combining &quot;wham&quot; (&quot;a solid blow&quot;) with the whimsical &quot;-y&quot; ending. The first example of &quot;whammy&quot; in print occured in 1940, but the word was popularized in the 1950s by the cartoonist Al Capp in the comic strip &quot;Li'l Abner.&quot; The character Evil-Eye Fleegle could paralyze someone with the sheer power of his gaze. The &quot;single whammy&quot; was a look with one eye, and the fearsome &quot;double whammy&quot; used both eyes. As you may know, &quot;double whammy&quot; has also found a place in English as a general term. It means &quot;a combination of two adverse forces, circumstances, or effects&quot; -- in other words, a one-two punch. 
  
 <br /><br />*Indicates the sense illustrated by the example sentence.</span>
        <ul class="links">
            <li><a href="/word/index.xml"><img src="/images/feedpodcast.gif" /></a></li>
            <li><a href="javascript:rssWin()">What's this?</a></li>
            <li><a href="http://condor.eb.com/word/podcast/wd20070401.mp3">Play today's podcast</a></li>
        </ul>
        <ul class="credits">
            <li>Theme music by Joshua Stamper &copy;2006 <a href="http://www.newjerusalemmusic.com/">New Jerusalem Music/ASCAP</a></li>
        </ul>
    </div>
    <!-- Accipiter popunder: 04/25/2007 -->    
    <script type="text/javascript">
    <!--

       if (!pageNum) var pageNum = Math.round(Math.random() * 1000000);
       var rndNum = Math.round(Math.random() * 10000000000);
       document.writeln('<scr' + 'ipt src="http://eb.adbureau.net/jserver/acc_random=' + rndNum + '/pageid=' + pageNum + '/site=MW_POPS/area=DICT/aamsz=1x1"></scr' + 'ipt>');
     
    // -->
    </script>
    
        <!--//beginning of share this links, link to page, and cite this//-->
        <div align="left" style="font-family: Arial, Helvetica, sans-serif; font-weight: bold; color:#000068;">
        <form name="highlight_all">
        Share this entry:&nbsp;&nbsp;&nbsp;
        
        <a href="http://digg.com/submit?phase=2&url=http://www.merriam-webster.com/cgi-bin/mwwodarch.pl?04.01.2007" 
        onClick="javascript:urchinTracker('/outbound/share/digg/wod/');">
        <img alt="Share this word with digg" style="padding-right:15px;vertical-align:middle;" 
        width="16" height="16" src="http://www.merriam-webster.com/images/share/digg.gif" border="0"></a>
        
        <a href="http://reddit.com/submit?url=http://www.merriam-webster.com/cgi-bin/mwwodarch.pl?04.01.2007" 
        onClick="javascript:urchinTracker('/outbound/share/reddit/wod/');">
        <img alt="Share this word with reddit" style="padding-right:15px;vertical-align:middle;" 
        width="16" height="16" src="http://www.merriam-webster.com/images/share/reddit.gif" border="0"></a>
        
        <a href="http://www.technorati.com/faves?add=http://www.merriam-webster.com/cgi-bin/mwwodarch.pl?04.01.2007"
        onClick="javascript:urchinTracker('/outbound/share/technorati/wod/');">
        <img alt="Share this word with technorati" style="padding-right:15px;vertical-align:middle;" 
        width="16" height="16" src="http://www.merriam-webster.com/images/share/technorati.gif" border="0"></a>
        
        <a href="http://del.icio.us/post?url=http://www.merriam-webster.com/cgi-bin/mwwodarch.pl?04.01.2007" 
        onClick="javascript:urchinTracker('/outbound/share/delicious/wod/');">
        <img alt="Share this word with del.icio.us" style="padding-right:15px;vertical-align:middle;" 
        width="16" height="16" src="http://www.merriam-webster.com/images/share/delicious.gif" border="0"></a>
        
        <a href="http://furl.net/storeIt.jsp?u=http://www.merriam-webster.com/cgi-bin/mwwodarch.pl?04.01.2007" 
        onClick="javascript:urchinTracker('/outbound/share/furl/wod/');">
        <img alt="Share this word with furl" style="padding-right:15px;vertical-align:middle;" 
        width="16" height="16" src="http://www.merriam-webster.com/images/share/furl.gif" border="0"></a>
        
        <a href="http://www.stumbleupon.com/submit?url=http://www.merriam-webster.com/cgi-bin/mwwodarch.pl?04.01.2007"
        onClick="javascript:urchinTracker('/outbound/share/stumbleupon/wod/');">
        <img alt="Share this word with stumbleupon" style="padding-right:15px;vertical-align:middle;" 
        width="16" height="16" src="http://www.merriam-webster.com/images/share/stumbleupon.gif" border="0"></a>
        
        <a href="http://www.google.com/bookmarks/mark?op=edit&bkmk=http://www.merriam-webster.com/cgi-bin/mwwodarch.pl?04.01.2007"
        onClick="javascript:urchinTracker('/outbound/share/google/wod/');">
        <img alt="Share this word with google" style="padding-right:15px;vertical-align:middle;" 
        width="16" height="16" src="http://www.merriam-webster.com/images/share/google.gif" border="0"></a>
        
        <a href="http://blinklist.com/index.php?Action=Blink/addblink.php&Url=http://www.merriam-webster.com/cgi-bin/mwwodarch.pl?04.01.2007"
        onClick="javascript:urchinTracker('/outbound/share/blinklist/wod/');">
        <img alt="Share this word with blinklist" style="padding-right:15px;vertical-align:middle;" 
        width="16" height="16" src="http://www.merriam-webster.com/images/share/blinklist.gif" border="0"></a>
        
        <a href="http://www.newsvine.com/_wine/save?u=http://www.merriam-webster.com/cgi-bin/mwwodarch.pl?04.01.2007"
        onClick="javascript:urchinTracker('/outbound/share/newsvine/wod/');">
        <img alt="Share this word with newsvine" style="padding-right:15px;vertical-align:middle;" 
        width="16" height="16" src="http://www.merriam-webster.com/images/share/newsvine.gif" border="0"></a> 
        
        <a href="http://www.facebook.com/sharer.php?u=http://www.merriam-webster.com/cgi-bin/mwwodarch.pl?04.01.2007"
        onClick="javascript:urchinTracker('/outbound/share/facebook/wod/');">
        <img alt="Share this word with facebook" style="padding-right:15px;vertical-align:middle;" 
        width="16" height="16" src="http://www.merriam-webster.com/images/share/facebook.gif" border="0"></a>    
        
        <a href="http://www.myspace.com/Modules/PostTo/Pages/?u=http://www.merriam-webster.com/cgi-bin/mwwodarch.pl?04.01.2007"
        onClick="javascript:urchinTracker('/outbound/share/myspace/wod/');">
        <img alt="Share this word with myspace" style="padding-right:15px;vertical-align:middle;" 
        width="26" height="22" src="http://www.merriam-webster.com/images/share/myspace.gif" border="0"></a>        
           
        <br />
        <br />
           
        Link to this page:&nbsp;&nbsp;&nbsp;<br />
        <input name="link_to_page" type="text_box" value="<a href=&quot;http://www.merriam-webster.com/cgi-bin/mwwodarch.pl?04.01.2007&quot;>
whammy</a>" size="88" onClick="javascript:this.form.link_to_page.focus();this.form.link_to_page.select();" />
        </form>
           </div>
        <!--//end of share this links, link to page, and cite this //-->
    
</div>
                        </div>        
                        <div class="content_footer"></d

```

---

### Post by adam_kimber on 2009-02-21
From the man page   > html2text was written to convert HTML 3.2 documents. When using it with HTML 4 or even XHTML 1 documents, some constructs present only in these HTML versions might not be rendered.

Your document is XHTMl 1..... 

The program does not understand <span> tags and therefore swallows them. As the document liberally uses them it swallows most of the document! Leaving white space. 

You could try tailing the file with a command like this. 

```
[tail -n 120 test.html > testtrim.html/CODE]

That will give you a file that works with html2text. 

Here is the output from the above file once trimmed. 

[CODE]

The Word of the Day for April 01, 2007 is:

whammy  \WAM-ee\    noun

      1 a : a supernatural power bringing bad luck
      b : a magic curse or spell : jinx, hex


      *2 : a potent force or attack; specifically : a paralyzing or lethal blow


Example Sentence:

"The nation's working poor have been hit by another whammy," said the senator,
referring to a recent tax hike.

Did you know?

The origin of "whammy" is not entirely certain, but it is assumed to have been
created by combining "wham" ("a solid blow") with the whimsical "-y" ending.
The first example of "whammy" in print occured in 1940, but the word was
popularized in the 1950s by the cartoonist Al Capp in the comic strip "Li'l
Abner." The character Evil-Eye Fleegle could paralyze someone with the sheer
power of his gaze. The "single whammy" was a look with one eye, and the
fearsome "double whammy" used both eyes. As you may know, "double whammy" has
also found a place in English as a general term. It means "a combination of two
adverse forces, circumstances, or effects" -- in other words, a one-two punch.

*Indicates the sense illustrated by the example sentence.

* What's_this?
* Play_today's_podcast


* Theme music by Joshua Stamper ©2006 New_Jerusalem_Music/ASCAP


Share this entry:    _Share_this_word_with_digg_ _Share_this_word_with_reddit
Share_this_word_with_technorati_ _Share_this_word_with_del.icio.us_ _Share_this
word_with_furl_ _Share_this_word_with_stumbleupon_ _Share_this_word_with_google
Share_this_word_with_blinklist_ _Share_this_word_with_newsvine_ _Share_this
word_with_facebook_ _Share_this_word_with_myspace_

Link to this page:   
[Unknown INPUT type]
```

---

### Post by meindian523 on 2009-02-21
Cool,that proves bean counts don't count.Absolute newb to HTML,XHTML,etc.....In the meantime I'll try that.

---

### Post by meindian523 on 2009-02-21
That worked,and a bit of piping helped avoid creating a new file,I just did
```
tail -n 120 /home/easwarh/Wordlist/Apr.01.2007 |html2text -style pretty -nobs >>/home/easwarh/output.txt
```That resulted in a file of all the words,and then I did a bit of sed to remove the > * What's_this?
* Play_today's_podcast


* Theme music by Joshua Stamper ©2006 New_Jerusalem_Music/ASCAP


Share this entry:    _Share_this_word_with_digg_ _Share_this_word_with_reddit
Share_this_word_with_technorati_ _Share_this_word_with_del.icio.us_ _Share_this
word_with_furl_ _Share_this_word_with_stumbleupon_ _Share_this_word_with_google
Share_this_word_with_blinklist_ _Share_this_word_with_newsvine_ _Share_this
word_with_facebook_ _Share_this_word_with_myspace_

Link to this page:   
[Unknown INPUT type]```
sed -i '/Joshua/d' /home/easwarh/output.txt && sed -i '/Share/d' /home/easwarh/output.txt && sed -i '/INPUT/d' /home/easwarh/output.txt 
```

---

