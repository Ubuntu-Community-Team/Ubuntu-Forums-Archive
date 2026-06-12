---
title: "how to get wireless g desktop network card working"
date: 2015-12-17
forum: Networking &amp; Wireless
---

### Post by Ka Fish on 2015-12-17
Zombie files had my o.s. in slow motion so I reinstalled Ubuntu 14.04.3 two months ago. My wifi was working just fine before that. I had two i.p. addresses, but don't remember the name of the drivers now. Now there is no option to turn wifi on & no list of networks. I've tried installing drivers & looking at many other post with similar issues with no success so far. Can someone tell me what codes do I need type to get it back on? Please take it slow I'm a basic user, thanks.

---

### Post by Hadaka on 2015-12-17
Hi, from a working wired connection, open a terminal ctrl/alt/t
then COPY and paste one line at a time.
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
boot,remove wired connection and test wireless

---

### Post by Ka Fish on 2015-12-17
The first three went well, but the last line gave me this.
sudo: moprobe: command not found

---

### Post by SlidingHorn on 2015-12-17
> **Ka Fish said:**
> The first three went well, but the last line gave me this.
sudo: moprobe: command not found

There was a typo...should be:

```
sudo modprobe
``` 

(was missing the "d")

---

### Post by Hadaka on 2015-12-17
Sorry for the typo, SlidingHorn is correct, it should have been..
```
sudo modprobe b43
```
I have corrected it above.

Is your wireless working???
thanks.

---

### Post by Ka Fish on 2015-12-17
I put that in & now I have a blank line. It appears to be frozen, but everything else is still running normally.

---

### Post by Hadaka on 2015-12-17
That is normal, it means it accepted the command without error.
again i ask you....Is your wireless working ok now?????
if yes, please mark this thread solved by logging back in to your
thread,first post,upper right area click TOOLS and then SOLVED
thank you.

---

### Post by Ka Fish on 2015-12-18
I do not see the the option to turn the wifi on. It used to be between Ethernet & VPN in the title bar pull down menu.

---

### Post by Hadaka on 2015-12-18
Please open a terminal ctrl/alt/t then COPY and paste..
```
lspci -nnk | grep 0280 -A2
rfkill list all
```
post the output
thanks.

---

### Post by Ka Fish on 2015-12-18
[ATTACH=CONFIG]266234[/ATTACH]

---

### Post by jeremy31 on 2015-12-18
> **Ka Fish said:**
> [IMG]file:///home/ka/Desktop/Screenshot%202015-12-18%2017:22:34.png[/IMG][IMG]http://ubuntuforums.org/;base64,iVBORw0KGgoAAAANSUhEUgAAAekAAAE CAYAAACp9egAAAAABHNCSVQICAgIfAhkiAAAIABJREFUeJzt3WmUJEd97/1vRGb13rNpRjOjkUBC 2hlMZsQSOxgwIC5GOPjDezH9r1 sI0xO96wgHPByzVg7oFjAxfbgPG1MWD8sBhkyxabkIRAGIQWJNGSRtLM9HRPb1WZ8X9eVNVMTamyKrO6uit75vc5p053Z2dGRGZGRWRERka6j/zx3xkiIiJSOnGapMNOg4iIiHTgxiuVRkvaAUazWb1l6zbOPvMcduzYQWWkMqz0iYiIHN8M0lqN fn93DdzGwuHDx35h5scGbVG/Vyvp4GzzzqXJzz iUSjDu99veJWp7iIiMjAOQdghNRIVgK3fu8b3HvPbfX/bZqcMucclgacg527dvOSF72EkfEKac1hqpxFRETWnPfgopTqYspX/ MfOTR7P3FlZBwI IrHRxFPveJp7N6zizSJcM2mtYiIiKw55wy2pjz60Vfw9f/4JPHU5DR4w5nHxxGPffTj2LptG2mSN0g7 sP1W6mXJQwREZHhiiqweWyKm6/7DPHExATee1JLcc5zys7dRPFojyAMX6kR QQfGXgHwUhTRwgxoVaBnq3wsoQhIiJSHs7D2M5RKhVPHEURzkGaOtI0ZXx0kqiSXUn7OGVsbIXK2DRxPIJ5j8NhGC4E0mSF5eUa1aVRQhqVOowsFo2BTxljGW BahJheELe7Y16i943frqjN/Z9o6XvcKQ4zI/gKsZoWKSSBlbMkVjEai8uDE9wHu8iKtESPk0JFpGYzx GOXAOczGuAiNumdFawrLFJOZa0ugwZ3ispUNDF0ciIv2q Jg4csQrK1VCCCQhJUkSRiojRCMjHTeK4sDktDE2sYN4ZLRe3bezQFJdYXnxMAvzEWkSlTKMbmrTO/HuPuLZw5wyMc6BmmMxrRAMzB2tmI4OebfGBUJdsPrvPorABWLv8A7MUlwawDmS4PFujNrYJlz8IG52iT1TFQ4lI8ylMSE4rNN NeLrVomnBo6YamUL8XjMZn8X40mNpeWYhTQi0HIsmiMDG/tlzaCtvo/Bj5GMTWHxLHZoltO2xBxcgrk0JsET8DgfQQQjLiFKE6qpJ3C0Ej8mte3xte J2TG3K8ys8acqfRE5caQYkYN4bm6OEAIBI4SAd46oQ XggOnNKZObtuIrY7gu933jygiVkRGiaI65/UcL67KE0cuhxa/wnlf/ET/a9Vw f9WVbFuKCNXAShoRqLdS6/Ea3ln9bwwLkDqP8zGMVCCOGR FEReIXY2IBGpV0pqRpBXm/Wbmlr7Ge17zVmZ2/ThffPuT2bEUUVuusGKu0XKPGhcGAe8a7VNzWMtFQVPzUbngK4SRaRar /j7N/waN8RP5 PvuoKdeO5ZGWEl9Y1DYXg8ZlYPzxzON1vFjtTFMLKZxeWv897X/CEzu57Pv77tMk5246RLoyxaROLGSSubiCcW2coco8sp81VjKa2QWEQwwzuP8wYW8HhoxFfPhJ76EWzujYcQ6j0BHrzV/2fkP38iIhudOYdzjnilWsPMCGaYGWkScP6hHbtjk4GxidF6V3ijYqxVa8dMdNL82zlHXBlhbHyM5dEVlhZ8ZhhZ8obxg 9/l/v33fuQ7U/euZuzz93bMYxewmSNFMBBFCc4B5UKmNWoJhE1IlylQsUFvEuJrFbvjbCIxMZIRyfxY54DN/1fvvjFL3DjLfdwOAXGtnHW3kt47tOv5Dnn7cSSiLmk2ojLkVRSJlYg9gGzlGpaoUqEVWIqLhC5gAs1fJKSBqilEaGlZR/MQ zqlXQ0ShzNcfBggO2BaLTG5HIVbAKi kWGJ8GHGiE4kuCouQrOV4ijBOeNEYyqj/G euR4LI2mnJwaUeyoEGFuitmlG/m7//kubp94Lh9//WPYYp40CSRhggSHjyIqkeEtEFmKJYEkRAQXkUSO0dgRO4dLawQzggukISIJnpE4waUJljrMmi30oxckkOKIwALmfL3HItdZFhEprzQJBHPEkY/w3hEw0jQlpClp tCpQkfHjHhsAny9q7RarfLpT36cJ1/5DHacvIv7993LNVd/kee/6KcYGRkBFxGPjlMZW LwnHUMo6ccYezbdx9bt25n2/aTjmx24MH97Nt3H2efd0HHMHox19x/x1I8jU1tZtSqTFfnWTg8xr54ApucZKqyxLhbZjSt4peWmF2aYDHeRG1ime9 4Ff54Nf2s 2iZ/L8X3oJp057lvffxneu RJ//j /zKef/av88U9vY7RlWtblaAI/sZXRsZRNK7MsLTnuc5uoTU4xVVlmKl6mUlshWl5iYdFzMK1gab3LOeBI4zHCyCQj0zHTozC9cAgP4IzEB0JcIRmbJo1HmB5NmXDLjCZVksUqh1bGqbopkslRJsdqTPllonSZWrpILQ1HjkfVj7E4fhJuxLE1WWLOPNHSHdx510Fmz/CEyVG2 AXSsEJ1ZZzF0c2MjMVMjiaMssRIskC6tMJcdZyVaDNh0jM UmPU1agYRNUFqouB2XSMxXgr0 OzbKoeZuWw41AtJgRPcPWeBOchMjBq9Za3pfWeBNXSIrLBhUY9HDsXYWbgjCiK6hV0h0q6MhoTuaOV6 jICFc /dl8 Qv/wt4LLuK7N3 bK5/xHEZb7mdHPmJkLCJJqzjcQ8LII08Y27dvZ9cppx752 M4eHD/kc7R9jB6sSMDvSqsVDZx12d j1d/9Hb8mc/mL37rhSSjNf7zPb/EP99wH8tAvO0R/PjLXsSvP ocDkRj3P/p/8EHv1bj8a96Ly/1/8wH/ Z9fPSBGlS2cM5TfoqrHv8f/N5ff5B37z2Pl5/VrABjkniam//p93n1x27Dn/lc/vern0MtrnH1e36Jz914NK7nvexFvOaSbSRhE3PVxm1eP04ytpVDD/4L//LOv SbP1oknpqi/iSdEVyFhcpODs7fyZc/8B7 /ca7mY 3c mzXspVLzuLkxYc /0Et33uD/jEp7/GvhWoTJ/Gi1/zezxte/N5vIhQmeaGZhrP gne84ZfxPuk3nq94yM85799BHgYb333r3Lqps0sLt3OF977J/zrjfeyHG3h/CteyFt 9mJ2jcHs4g/5 3e ixtvu4e5GjC2g0uf kLe8JN7mXJj3HHdn/AH7/tPdj//V3n3M06hVh1lNo0JvkLNx4xUIiouxVMjDY7EQZwss1SNC UxEZGySdMUc0YM9a5lH9XvH6aJQVt3t/c0BgcdO r4pO0nc/Glj GrX/l3Hv EJ3PS9pOPjSWKcL5 zxOzh4Tx9a9cww/vuPUhiTv9jLN47BMuzxVGnWvrPm/83lzWEkZIezezgh29P/rDr76ft370duykx/Fnr72M01zEtyubmBzbxhmPOoNNYYYbbrydf/qLT3DJe9/AnpHr Oyn7mL6KW/k57b/I2/43S8yd oTeekv7OS6v/lHbrnpQXb 8m/zks//Ch/7zA285NVbGqn1/OirH QPPnYbtu3x/OnrL MRLuab8RamxrZx qPOYIvNcP0Nt/PJv/gEl/75K7l0PGI5qgAxiR9jMbqNz7zz3dy4DDvOvYjd1bu56XA9bGyM2TDLZ9/2Or50f8yplzyGMx 4gRs/8xf8 vTv8KGf2Ibd8iE /PdfY37qbJ5xxS7C/hXO2NLaf yY cr/qafxpCfwx2 6grNH4KbmXYSR07j8cbuYHNnByeObWXDzfOGq3 HL98Pkaedw9uIt/Ne/fohXzr ST7368Ywu3sUPvncPc2zjokt3MX/rd7nxsx/glbO/xF /6iTCHd/mkFWZu2Uf7jknU7GIECosuXHC CS3f X9fOOOKnuf8BSeftHD2Pe9q/nGzAiPO/eRPc xiEiZpYlhBnG9vqsPQooj37ElnaaGWX3IVGvleO/M3dx043Vc/pSn8c2vf4VNmzaza8/RFm19MFUgqabAQ8N47BMuP1oZZ gVRh7HhtFb8wkq7vs8b/mTwyxOXcxb/vD5PGHE8935McLIbh7/O/ bF1UOYLV5rvujV/C26x/guoMVTku xG3JOE98 sPZ97k/4RDbeeXrf5Fn7kzY98l/5HYCRKdx7i4H98ywWJuuR3rf53njHx9mceoS3nLVC3hiJXDboRFqk9t53Gv/khdX7sdV5/jGVa/g7dc/wNfnR6le8z4v0FPIYfO4NnPm2J7yyDv CVfOSqp7Bw4L/4nVe8ndsBcxMcuv0T/Of94Pb Mm9/7WMZPXQtb/rvH AHV9/IAy84jxG3XL/3PHEKey9/Pi/aO8HoSsRN zmSxjf88WEWpx7Jm//ohTxpIuWOec9K87DueRKv 83Hs6MauGtpB9 /5QNcez9w9sv56DufC4t3847/5w1c /V/5erDj X8uHEOdz Zt/zuixmb/x5veOXbuPnaf WmVzyK837qnfzeud/itLN34msp86lnmZjlsW0c sG7 MAn/o0a8I3rruZjOx/GlgfvYt9pz UxZ12cO2 IiJRR87ZzHMVxvQvYQ6VSIaQprkN39/JClcnpFB/Xm03VapVrr/kyVzz1WezYuYupqWn /ctf4AUvfln9njT1PvXlhdqRvvX2MPLoFYYD9h944Jht9h944JixwO1h9HKk4WiHWQTYvJPTNgErFQ5H23HhZv7tbW/kU9fdw9KRrTw1i/GLD7DMFKdtdlQXa8AoJ1VqLIS4Ea7DWcL8isH4FGO La4tuzh1CqhWmPMnE9ytXPO21/GZ9rhCxPxd3 aOO46m 9GXVEiALaftYJpFDiWVxgArB0QsPHAPKwDffR8/ zPvO7rh/EEOJjVGzvgVXvbUb/HhL/0b/ vN/8Z7Tn0iv/f6n P0Rqd5axpPmwaqCSuNq73mkYuSRRbnJngwTLNwoB7fljNPZTtLzMRnc Z2uPbwIX44l3DhxJGH1nBJwvLkJVywE26emefuuXkes2UHE4 8mPGFfeybd8wvQzISk/hJqg usGPvK3jzax/FfV/8Wz78D9dy58R5/L /8kjCIb1 VUQ2tpCmmFl94BgY8cgIU1OTpGmA5KGju dnE7ZsX8FX6hXwyOgoP/GTP02lUSGfvOuUY/52DpKlZeZna6SN8NrD6CVPGDt37Wbfvvs4eODAMdvu3LW7PmlIhzBy2/Fkfvr06/noN77Ab/zpDj75G49mJBrl4Offwsevu4etT/p5fudZp3PH372Nj3y7vkk8Nk2FRR5cgEsf TC4/od86st3sPvKbdQCUD3Mvts xxdugx3PPY9t8eKRuH7m9Ov5m298jt/80x3806svZdRVOPj5N/KJ6 5h6 U/y2ufeTo//Lt38OFvA a57K3/zNOjGqO2wohVueW69/N/uYXZ7/ I 9NziN3K0bHQBhPbthMDyWk/zlt/ ULG3QhmKZtiOCMxbgmbeex//yBPffk3 be/ficfuPpa/uj/PJq/ oX0SBp/9vTr cg3/oXf/JMd/OOr97IpWsYxUX/yemmJeZtgYsQxUa0yuW03I9zM7K372J9cgFv6Prc ADDNaZsqhGrzMbIIfIV4 U5mDgJMsGtqnPnkAN 57mZOecQOdjjwlhBWVrDReU555jt4xwtn2RQFdrzgNbz7hQmT4SCbF /h8/sLnmcRkZJJ0wDmia0xPZb3jpGRkXoT2z 0JXLw/pQt2 fYOjKOi oDcyptk560/p2mCYcPzXPg/uUjLa1OYXRPZO8wzjn/Qs45/8JCYfSUNNrg8Xae 6o3M//br cz13 c115zOm 6YonRuD5w7dCd3 OGGw4yu7/eYnaWEu95AqdyDV 75i5e9nO/xc989XX8zcfeyW99rBn4l3nj67 Mf/izeM LziAsfudIXM//jTcw9 o38enrP8prrn44f3jlCuNRI64f3sL1N8wejStdZHr2Xg6lFRYsEFzEyukv58e2XsO1d/w1L3/V9Zy/dZY7AQg4W2bi7Jfz2M3/wbV3/zNXve9Wzj85YmV2jtN 6td47Y4xDv/gz3jP393O7tO2ED9Qv3iIvCNqzrUW7 DHX/VaZn/7d/n09X/D665 HX/2pDnGtuxl9xg8cN neNVbb d0P8aTf/6XOe2sn OJO77I1bd mJf xrXsXvwBty/A6KOu5MpNFe68v3FI7v08b7zqTib2fZtvLYI//wn82PQ4X/mr1/P2L zHnfdSPv1L5zPhYX5lAXdwhmqY49DoIgupEUbHiKOEybDAfYfjjk8niIhsJGmzJZ2kSX2KyqQ aCyrkk6BH90 T1zxTG/bgY8q9cFcbZxzhNoKh2f3c/dt8yQtjxiVJYxeQq3xNK4FkuhcfvK3XszX3/APfOtDn AbF13Mw6/8Q15 65v51Fe/xqfvBqiwdc9ZnD9mLG99Gs973J/z7sn48/5u388ts yIt dCu3LZ/EzjO2MXb395i1LZx1ygRbEvjmXDNWw KzedFvvpivvfEfuOnDn ArF53L7iv iJfd/iY c0xcZ3LhaBW3/z5m50dZspgkGmVp0xk8901Xsekj7 Xqb32X62fAjW/jnAt3M12tsj89kxf/4VVs/fD7uPr673PDvVDZ/DDOrtVYCp7l5RT238jXfhiAMXZf/Cxe84tn4xdvarTIU LobF78qhfz1Tf/A9/68N/zpQt jV3Te3nBr/8kSx/4B35w87e5b J0LlqZ51w7lee8 W1M/uX/4os3/YDb3WbOecoLeeMrLiFerLBw5IZEyr6br2euGrPjoufwplf9GHFtgsojzmczX Xks06u3xaopZDU8GEeS5c45FKMgIs8zjtmQwqJUyUtIhtemqYEM9yO7XsMIiYnJti8dRu/ 2uv7Tp39 R0hYedPc301q1Uxibx/uj95WCB2tJh5g7Mctet8yzO10odRqbTL2bnyYs8PD3IyuIoD45sZ3r8MFur9zB/aIR74tMZ3 LZNrLCmE9xboWRlYNU58a4Zex8Rt1X ewfvI7P3uk55VFP5amPfgS7pkdIlg5wqHoqL33aGVQOz3Nw1nOnO5XKycYZzOLmHT KdzA5tsK29D6WDsGP3OmMbh1h 9gyYy7BscJY9QDR/bPcfj/sW4mo1jwhigmjW6js2MGWbRVOmlhmKjJiV2N85R6WH1zhjsMnMT91CtOb4aTxhCm/QpwcZnx lrtnR7mnci5bT6qybXSFMVdlrHaI2uEl7q7uorYl4lQ/x/ihhNvZwehEYEe4B5tb4Y6lk5nfuotdm5bY5g8zVp1l5eAi9xzewsHxnWzZFrNtfIUpVqhUD5HMLXFv7WE84L7Gu3/rXdy3 yf4xHuey84QUVtepjq3wJ3z29g/sYfdk/exY2kfc/tWuGcWDqcRgfpsbJEZgfqUq2nj/SoQqE aLiKycaW1FT78oVcRB3N470iCsbi8nNmSbpqbTbn5myvs2L3Ilu1jTG0aqz/eFAKHDy1x8MFlHrxvCesyo0RZwsgS7rmDA4dSlkMVap6leJ7ZKOUBqtQWl1mMbmfx/pjDMcRxigsJLiQsLycc2rSfqVN/jJe946943Jf/ns986et88i8/z EAVCY49cJn8/QLpwmzCQ/MR8zZXfhZT0oNW0lZjJY4GAceZJmwlHCYO4j3xSyMOCpxiiPBJ8tU51IOVx3VtDGlZ1LFaglp9TCHZitUG2mruICrrrCykLCYHmRl/wK18QpLI444qlFJEqy6zMJSjcPu 9QOOg5HRsVqkKyQJLCQzmD7R0ioYUsrHGaJqBIxGxZIlhOWkvuozc5x7xjMuwRshXQhYaG6n2q0QLI/ZiE2Rn3AhYQkiVgchXTqaEu6srCfpf0pdx0yFhZgrvYg1XiJ 0ZWOFCtkiwZi4knaXnNSfPp7XAkFB7ym4jIRlR/Ttrhtm9/uHnvwUeMjo7wzt/ /a4t6YdwEHlfv8ndr7KEISIiUgJpbYW//tvXEHsPzhkWUlZWVghJAFesoktzv8Sx/GGIiIgMW2g8jRR77/HeYwYhhHoTu0t3t4iIiKytluekIYocFhwJjjQNLS YEBERkfUW0kAA4qgxD3b91YWhUUmr21hERGRYQhowM9zDH3amOecBR1IL/Oieh77wQkRERNbXsx97Kr75pijn87/mWURERNaeJxgeV//4/G WEhERkbVjBt77 Mhrl1VFi4iIlIM58A7X8cUTMzMzhQOcmZk58llNOHnjWs/tBqHbcSmSrvZjfDzYiOeziE7p7PR96bY8K5y1To IDIeZ4b2PGpW0r79Xuk8zMzPs2bPnyGcjftHXMs3N49Ot4M1bQO7Zs2fg6Wu3Ec9fWXU691nfl27fo255aK3SIyLD5aMoInIeb0akFxMMTFYh1ywAmxVt6 /NArIMypKOja79/K6mx6BM4YjI mi8T9pDlyk1W7/Yzb bOhXmWV/8ouEUCbdTOHnS2VpZtv7sFU57Wjqt314gdkvLIPSbzqzlq0lne2ut/aKkWxzt WRQso5PVnqKHs8iynYRVLb0iEjDWWdcYGeevtfOOf0CO/v0CwwwwGZmZo75mfVpX6/XzzzhtH86bb/a5Z3Sk2dZr/C7hdVt31v3Ne82q0nnoNLf7Xy1hpFnedHjVjSd3fLboI5b0fOUtU5WuorEW R71G/e1Ucffdbu8/RHn2px5CsEUujw9qisFk3RLrIi4fRzRZ8VTmvrqL2FtNYthyLht3aB95u2bvubd/t dNsu639Zy9fjvHSS1cuxHl3BnXqXBpFXu23Tbb GdQ5EpLOYEHA4PBGGHfPPTpVGty7rrHX6DSevXpVBnvQcD7L2d6Mo23lZ63SU4aKk9XtXpmMvIoAzvPO 63CxboNLslqwnb7oRcPpVzOs9vuJne4l9mpR5Imr Wnf57z71NyXu/hWS3/e2WzqLpXWtrNZipGW7r8S6i6PFsj7e5Xb8XUlnhDIoqaJHyMTNi5wznwQUPbS3pptYWTnu3aqffW7crGk6WrHXal2eNXO124dBpmzzh9Krw8hbiedftFn7RdHZbfy0rgzzWqkVdpOemn/PeK6xeF3Lt34tO8a7lOen1/RWR9RVwuAvOutgAXHCA8Z3bbxpysjaGXoVlWVomZUnHsA3qXq Op4islysfvYcYl JwOA aGHRwVJCXS56eFRGRMjGD2FzAOw pKugiNkohv1HSuR4GcSx0PEVk3ZgRg8ecw q93SKlM6wWsFreIjJMZoY3PM55jPqn3aBGZGc9qlV0tG2RUdP9bLdWhh3/IGSdq35HTBeR9dRA86n/Tsva/5e1PCucfp43b9eax9fruev1sp77tdF0Odlucpr7KeMMiKo1uaiu5Dt7T0G35WOJ2W91vu95uOtcjT/XxXnHNw3nmX2vnnXWLnnn2RnVsfRHbkM1Nw9qWsT6f1s8IsGk63dbvF1y38tfisZdjrGXdWWMM4dtb2oe33rHXa18taZ1D7VjQfluVcF4lnmPl7NcdkvfJt0bK0U7ry7scgyttu6w yPM/az37zV7/ns1d8g8onRcO54pF7zLtolCgexfsRfFShqXUUa9Yzmp0ei r0d7f18xpUOHJ8sMZPx9Hhjpax7lqEo/x3rI16O2DY6c569LFdt/zWWjbmLSdXMx/DoMvzPMtXE YgDDOfxKnFGIbhiPzq3oLVqSIfpjzPp7Zm7tafWc8vt38hOoXT6Xnr9vjzHJ9O4ReNt9d dUpnVrxF9Xt8VmM9hj8OIp/3c/zzLO UzjzhtKZjtd/ffvJnkXQWOW5Z T9rWT/xDkrrsW9NQ6dl7f8btn7mDigaTtFyadDlWKd6YBDlZ7f1A8CZe59iZ 293M4 /3Lbe8EVPZv7RbsFenWbtH7o0uzvt7sm62dWevLG2215t66hfrtt o232351S2fR4553u27pzHssoHv3da91WpfnCSdPvuiV/k773c/xL5If lmeN58WzQdF93e1 SdvHlvrfFs0vZ32v9sx6RV e/rzlLX9hJ8nbwwiHw3q7yLHv9uxz5tv /37yY/cY3E0MgmW4szwUcxqFbliKTIDVL/ydMnnMVPgijVrdqoiYXQLczXrZK2/FlfjWcd5reOFeg6Hh3Zht/5t9K/fY92aB4oeh9V8R8rW2lpNerp9v9ZSP2nO6pHLG0e37YqWLUXWb/9/3vSvpozr1zDihMHlw17rx5u2nISlCWktpeJPjGelh1VgDaIrcSMZ1n62V8jHg06Fphx1PB f1n0pc/lR5rStp0F1/Tf58alpxiY2MTW9mcro DEbNjNH 9V/p VN7V OrPV7fYnyhpNH3vsceZavVr DLQaVnmEVXoOOt1OL2FG8gs4Kp5dhVgLDzD9rEf7MTP4Xlqw2LWWrvHulZ8 ePUc zb 7bbeacjKPbuV5P XsamXF20xn8zMsg2hVx86P4uMUhz3kldJZLb s5VmZo9P67ZVVp6vgPOEU1S3eTgMB2gdzdLpYaQ8nbxq6bZMVfj/xFhnw0s956XUxlzedRXWrlNu7spvrWtuyXuF0UqQQbF0X j/ 7eew0 9Fw mUniK3dAaZP/OGnyc9nbbtdPzXMt9mnfdBhZ nHMtb3g4ifMgeBNirkZZ13tqP3WryVZ6LoU7lfFb6e4XTLQ1F85u77CdeYy4Y3jmq1SWv 9t2siehnk1bC6TgQGN0pzkPEqfw6GjuOJYb3Pc6eKdiPmsydfegpxslLFGmNakyRZdaCDOhAb8YDK2hhWXujV0yEi az392U9evLWS1ytLmMhEEIgTVdfSYuI5LWRC08pt Mlb8WEKpamOPOYpcNOj6zC8XLlmFe/ 1v2rq yp09E1o PAGcGpDgLvdYvrOgo7l5/Z4Ux7FF8rbLSsh5pbB0J2h53lkGMQMy7fuu5aj8e3c5j1uCoopXZsCrATvk66zhkDQYTkROPT9KENKTUqjWSam1dI28dTde vGgYzc9qCrdBFYxZlcCwWkdlKvBbz1WngR2dzmNWPtkoOqU/6ziIiLTywSA1CBgd3lS5ZroNQ18NFXjH6tVyHFQruuhz8XW4AAAZHElEQVTyPGlrX2cQF2HrnT/ypL9TujbyRYmIDIYB3sfjRPEIlZExRkdHj1khq/txrbuXB1VAZXWptv6v3 VZ4a91OovqVUFndY1n7W 3rvS863f637B7GfKe39X0 mTFrwtLEckSj01NUV1ZwVvA 6NTPWQ9Z7ZRnj/rls5Ov2c9oJ 1/qCOQ9F0rrV 9qvbscuKo1vY652n1vL89op3rcIWkeOAg3j7ybuprixSXV7Gc3TgWGtrtvW WdbyfnRrhaxld1/RNK91iy9rP9cy3l6t3CLrQ7HJPrpVfsOosLKO81p3Nw97v0Wk/OKTd 2mVltm7sB Qttz0lmtuEG17tazQCyzYXf1Nn9vvRArsn7R8LutX6aKqlNaWlvZZUuviBxfzMCPTYwzOTnF9KYtjE9MHvln 0jUTvcd13pwS7/dx4MwrIuG9Yq3fWRxr4q51/rt6c5av9sAs26VYrd18lpNfu13u6z09wpPFwAiAhB7DBd5pjdNs7wYHflHp0dGui3vplMBPiiDTGd7V34/8UL2vcZOy/tJZxGdBj316rbu9/wWuX/dKfysfDKMVmu3dBZNT6f11/q8i8jxwf2P3/9biyoRlsLKyjLvv rnh50m6dMwC/1htPz63d yt1LLnj4RWR9PuvQU4rkD 5mYnsT7CAuaFnQjG2bBPoy4 42z7BVg2dMnIuvHz 6f4dCBfYTaMpFvfwuviIiIDEtcnTuAD1UmKhFjE5uGnR4RESmBE23MRBn31xnEi4cPkqYrxD4iqa3v3N1rrchBP17vA/YzaK/TALO1Pj6dRjtnjcbutLzbqOk8 7HWE6sMKt686VnPyVjKPBZhUINWh1k rEXlkXd/uj310esR2k7fyaxtip7HTmGt9nuU98mLdff4y55nl13xErvyWb9gL3jZq436dKEb/jMzM9P1717rr0eahnEs8qZhvY9f1vbdws2zX53Wydq3vMv72bdOYaxlenqdv0HlxfXO0/3sRz/5v8h ruUxGOZ56/adylseFM3b/aR/0N jYZXTnT6XX3KKeeccpAmLC3PMHzzA8ep4ayWX7WqvjMe3/bnkTo 9FV2 mjRkLV/P9DSV8Xz143jZj7yGvb95WuCD6HXolr/L8L1eTzHBCC7FCCwtHR52etZct27AIt0yRcNpzSR5w2/ ndW1tNovQ7/daFnp6XQ8BtUlOqyu1byy8kMZ01v0fBXNJ0W7N9eiOzePftPT6bte9HvdLfzVpD/veezXepyfQZVvx4s4pAk4j3OOWro07PQMTD TRWQVWkXu7XUrrDtt2y381m2ylufV/qUtul/d1su6Is264u2VxtZ09hNOkfWOd6s9X4PK/0WXr7V 09P d7/f66z1isjzHem2X2sh6/h0SntWGrqVbyfi9zoOJFjqcM4NOy0DN4gvQ/tVaa8wiq7fTFs/6epn/awWfx5Fj2G/aVxNGNK/9sK1qZ980insTt Lfr4v7fH0m0eKpLO5fpnyY7dKrtPvw1K0N6X9fye62MwIIcW76LisqAehVysuK4Pl/VIPK0P2U4mWraDqZBhpzOr1OB4M4mKrdXmn1lan5XniWU2LsJ90luXcrlfLuIi1PjZlOfbrzSdJSrBAEmokSW3Y6RmYPJm26DrtV9kzMzNdvyzdCpGiy/tdL6 84a22YCxqUHG1prvTrYO8ywelbOnJq99Wddb3Iu/3Za3lTU vNOYtUzqVHUXSWTTOYem3nOunPNpI36O8QjDcxZc 2eqjvetuuvGaISZpsHp1rbS3flrl6aJpj6tTN3Kne1V5wu92TytPejqFnSfeQaWn6L3Gbv/PCr/bfuU5T6tZniVPCydPWgeRnjz3I/O0Yovkk0Euz1K2/N 6zWqOc559yFOO5TmP7WFlrZ9VfnUKJ09P42rzyXp8r8tUeT/p4t24Cy 63MyOVtI3f c/hpikjaNoJbTW8YtI W2k723Ri6dBxz2MOJvKco4uu2h3/Z50/b50wOuedG7tre9h3AMVEVkrwyxjhhF3GctU7x1xoFEx 4jUwnBTtMGU8aSKSHmpzJCi4uYvzgGmlrQUN6wehTJ2T4nIsU6072m/ 9uxi9 1tKTNrGX4WI8NuywvlIA 5A2nn4FOrTZiZuo0eKXb8kEa1CCMIgOvss5dEVn5pNcAmfZlveIosv6JZlADJ4sOKFvr8qFs530jlQ95y4FeAzOzrGW8/ZRLmeWkGZxzweV2zt4n2VnnPdHOPO8JA5mgvP1TdP1BhJM3zTMdJmofRFr72a 1DGst96dXnIPMJ53 t5p9m2l7WUCvNHTLP4NYf5ifosd9LeIsWub0e3zXunwY5Hk/nsuHbt/nfvJjkbqhn3ptNXVQP tefskp5r2BByLniZ2nqbVmb71yyFreul37393Wz2tQ4bQrwxXu8ajo cqzfpFW aDyRy9F889GzW9lTfdap2tQ4Zf1 A1LnpZs0XKg0/K89dGgy58iuobr3NF70gCtj2L1G1nPSDusDxszExfpdmvvRm3vEum0vNP63eIdRPq7xTso/aS/nwo67za9ni9dK/3kk/b1i4bTbf3Wn53W71YArmf 2ehUPvS/XT8V9CC 293ihbXN50cq6eajWKtRtLDLuie0ltqvkvq9P9Oe3tbM2 1eV/vv3Y5Zp/W7hV9E0XQOSj/pH1alu5YXkf0c/0Hkt6xwuh2zrB6ztc4/69Ub0mpQ5UMWlQ/9yyoHspYPuhzIe0wGLe69SjFFEjqMLyF0vzjo96DnrTyK6JSuQco6/msdb1ZcedYpUlEXTUe31up6GtTxzwpnrb93gzpu65nmbvEOonwoGm/R9Y/X8iEr3l4XnYNMX9ZF7Xo5ppJezxdsZF0NyfoZViUkw6PvneSl8qEcjowUc 7Y11W2tizar1q6dT92ao306q7sVFD0E04ea1UoDSrcYRWag4437/lq7T7stH6/6epnu367Bddy/fZtm59BFKDd0rJRKu9Bp1Plw3DjLVoO9EpX3npk0PEW0akXr8k5hzt372X1G9HmAOP7//WfD0lMr/shrctaI867fvu9g6LhZMkKp9Pyfro6i4bfrVum/V5XnootT7yrTWcevdI6qHzSaf1O2/Rav9e2WV aPPkzK45O6xc5/kXzQ5ELo275cLXpz5OfioZTNJ8XibdbelqpfMgvT2OuU9x5y4F 8sMg6rWi5VI3WesZF7cOdd8CTDDDOHWeCW712bK9CikQ0rHFl7RQvH9Yj3eMs/x9v yIljWOVDM 5hxNlUJO5Oaa1X0nsvNzDqA7sf2pIWkeFTJS1y4nnKo047ek9aRMpLFbTIiWlDVdIbZTCLiIjIIJSiks4zuhu6j4ITERE53pSikm6nilhERE50Djf8Srq9Qu41QEataREROVFkVtKtD3Z3qkjbl3dap5dOFbIGyIiIiNR1nbu7fQKBrMkPVLGKiIgMXlxvTBudpu3Omqh8EN3NqtxFRESyOdfSknbOQc43VXaqXFtb2Xkr4PbuclXaIiIiR6164Fi/reo9e/Yc TT/zhufKnMRETkRHGlJm VrRrePrm7vEl9tJdppMJoqZREROdE454id8y0V9NGKutdjUP38L8823bZXK1pERE4c1t896WFRBS0iIicM54hD/bey188iIiInnLZ70qqqRUREysK7KMZFUf3jj85t0s o7TwzkQ1Kv EOc0rR1c7QljeO1R7/TrPMdVteNJxhGdR iYisB8cAX7DRHNTV/GzEQm8t09z6DHlWvKutLFrPQd5wst421knRMQG9BgHmNajzMqj9EhFZD84ZHvMc85GByKpY2h9Ta/299bnx1cobzrAqKFWMIiK9xa4xH2gIIfOWdKf5ups6FbZZFVTRcIqE2ymcPOlsrSxbf/YKpz0tndZvr4C7pSWv9hZ5kbCyjv96V5hZ8XY7zkXSWjRfiYiUkXMOzrv42Xb Jc 2cy56hp1z4TOao8dsZmbmmJ9Zn/b1ev3ME077p9P2q13eKT15lvUKv1tY3fa9dV/zrNvruOU9j4Na3uu85j2unf4uGmc/52U1ceijjz76rMXnmY8/3WLvXeZsY1mThxS9R1gknH5aPlnhtLa 1vvNXUXCLzrveadWebdtN8IkMN3OV1EbcTyEiEg7hyNu1s/eeYxjK s8r6bMGgjVa7rQPOHk1WtAUJ70HM82yv5mna8iBpmvRESGzbuWd1Rmva4yz73g1vW7vSUrbzj9ar HmRV3rxHQedLUHI3dqVIpMrq60z3sQSv7iPte56vTekXCFBHZcJzD7b3keYYLWBoA47/Tmgc4ukfTBPp5HKrXq1oLPCyZI1WKvIwLG8Lfqi4WSlc9Bv9 oVb6eLhV7Hvz2dRZd3S ugwu90XnrF2y1/rma/RETWw3MuO7NRSQNYilk4UklLd70q1Y3QvSwiIuX1nMvOJMbVZ 828537u6UvqqBFRGQ1Ilz9OenmcDGnSjq3YVXCWfdZdVEgInKccY7YXIRZwHvo/CCWlE2/g9RERGTjcM7w3nuc8w9pRfdT8LeOdl5NOHnjWs/tBqHbcVFFKyIi7TzUu7mDY1X3pJsDpfSCjeyw1/oFGyIicvwwb/XnpJsfGZxu947bHwtaixdsiIjIxuYN4kBj4Jjz9SUddJvFSS/YyI63vQLulhYREZFWzjkac3c7LASsQ2O60/O vSYD6dStmzecbvNw96oI28PJk85ucfTartvyvM9Jt 6znq0WEZFWMc6DM1yHGjqr0ih637RIOP1UUt0q9ubv3SrotVAk/NZKXRW1iIgAeAdx84/6LeljK2q9YENERGRInMM7X3/8yhqfdnrBRve4mp yv2BDREQ2lsY9aQ/mSAGX8V7p1pZnezdyp99btysaTpZe96vb48xanpWeTvvTK5xeL9jIU nmeWGHiIiceBwOd mTfsYwI1gCZtz0lU8MO10bwrBesJFncJuIiGx8L3naOcRmhiYEHby1rDQ14YmIyIkhdpEHM7zzWEZ3tzzUsFquajGLiJwYIg/e /psY2amSlpERKQknEHsncciI6SqoEVERMrCHMRRHIMZKRBCGHaaREREhMYjWHFUr6QdjuBUSYuIiJSBc464ElcwDB9FmFrSIiIipeCAeHR0lGD1yjmk6XBTJCIiIkCjkq6MVOotaOfUkhYRESkJ5yAeHR/HQiCEVI9giYiIlIRzEfH42BhBlbSIiEip1AeOVer3pC0EVdIiIiIl4THiuBLXu7stgCppERGRcnCOeKQyglk40uUtIiIiJeACcRRHYJ40TXHODTtJIiIiQv190rH3/sgC71VJi4iIlIH3njjyEebAYQTzvbcSERGRNeccxC6KMAJYhEMDx0RERMogco643op2mHeojhYRESmP2Ll6F3d90JimBRURESkDM8NrRLeIiEj5OOfwZkbzIyIiIiXhjNjMCKE 25iZurtFRETKwAFxLQUMghkhqDUtIiJSBo3u7nrrWd3dIiIi5RKnAUJIqQ8f0yAyERGRMoh8RBxCwAzdjxYRESmZuF5Bo4lMRERESsQ5w3vv8d7pDVgiIiIl4p0nxnlozNptak6LiIiUxpHXXml0t4iISHk4B/HRPxy6MS0iIlISzhF77wkh4L1HlbSIiEh5xOYceI h btFRETKwkeNe9LOOVzjvdIiIiIyfA539FWVakSLiIiUh3MQNweMeed0R1pERKQknPfNStqBU2e3iIhIWfjWStqpJS0iIlIajpbJTERERKQ8Iufrk5nUR3ers1tERKQsnHN4GpVz8zEsERERKQEXGtOCHmlJq5YWEREpA /90eek1eUtIiJSHg53dOCYc04zjomIiJSE8 7YV1XqfdIiIiLl4AHfnLNbL9cQEREpD cg9s5j3nB6C5aIiEhpOOeaM46BiyL0PmkREZFycN4TR43K2ZIU7zUBmYiISCm4xtzdBtQraxERESkD5xxxJYrAwHyi56RFRERKwjlHHEcxRgrEGjgmIiJSEr5 T9oBERasUVmLiIjIsDkHPooivPN4j7q7RURESsI5R y9w3BgXpOCioiIlIT3Du g3qZufkRERGTonGtU0g5Ag8ZERERKxBHj6uUhUtIiJSHt77eiUN1O9Lq6oWEREpBefs2FdVhmGmRkRERI7w3uENCEAwR9Bj0iIiIqURhxDqregQSE1taRERkTJwzhOHACE1UuoVtYiIiAyfcw4fgmEYZvWfIiIiMnxR5ImTkGKNbm6nOcdERERKw2u bhERkfJxztcraefrT2Kpu1tERKQcvPf4 oxjDtf4KSIiIuUQu8aLNRx6VaWIiEhZ1N C5epNauecKmkREZHScC0Dx/SqShERkdKo35NuUEtaRESkPLz3xDEec4HEe/QWLBERkXJwTs9Ji4iIlJYPDszXu7q98723EBERkTXncI1HsPR8tIiISLm45ujuRpe3ur5FRETKwblGS7o505gqaRERkXJwzhHjHM4ckfca2y0iIlIS3rVMZuKjCO/VkhYRESkLHwEVH ENvJrSIiIipeB84zlpM6s/gqUnsERERMqhPnDM6s1pHCGolhYRESkD5xyx9x7DwEz3pEVERErCe0/svAdLiZwHF4adJhEREaEx45j3DizCezvyvLSIiIgMl3PUu7sxwzvDazITERGRcmjOOIYL1MeO6RksERGRsvCO tzdZobXM1giIiKlEddfKu1xzsBUSYuIiJSBcw4fOa8Xa4iIiJTQkaazc2pFi4iIlEmM1ScyATDTwDEREZGyiH0UYeaAoKekRURESsI5RxxFEWbggscsHXaaREREpCGOI4/DSGsB031pERGR0ohjFwCHrziSVC1pERGRMggYPvYe5w3n61ODioiISDnEzjti8wQg6HlpERGRcgh29AUbBIfTtKAiIiKlEdffIF1vSWtaUBERkXKwYHij/nINs0CwMOw0iYiISEOcmoFBMBqTmoiIiMiwGUYcAmCGmZFqWlAREZHSiJNagmGENMHU3S0iIlIKziBOgkFICGZYUEtaRESkDJxBHIIRQr2CVm 3iIhIOZhrvE/a4etvrES1tIiISBk454gND87V29VqSouIiJRCCAFvjZHdzjkgGnaaREREBDAzvDlI1c0tIiJSKiEEvHMOTQYqIiJSPt6ZwxGBGZpvTEREpBwcrt6Sdq4 isyr21tERKQUzAzvnAGNgWNebWkREZEysGDNlrSrP4YlIiIipeGdM5w3sBTTc9IiIiKlYGZ4D41npAHdkxYRESmNenc3YM7Q66RFRETKIbXGc9JQb0073ZcWEREpCWu8YMMBqJIWEREpCwuNycaa48U0cExERKQc6nN3W NetIHXnGMiIiKlYAbejuniViUtIiJSBmZGjPn6vN3OA2HYaRIREREgYMRQH9kd Uj3pEVEREqjZVpQ72m0pkVERGTY0jQQ40L97VfOEWnGMRERkVIwM IoAhcgWIqPVEmLiIiUgeGInQWcd8QBUHe3iIhIKQQzYu89zhsOrxnHRERESiJNU L6wDHAOZxXJS0iIlIK1vIIFk73o0VERMoiGPVK2szq84/pOWkREZFSMKP go0QApgjaMIxERGRUghpIDZSzIwQAqm6vEVERErBrDHjGEDAY mQUyQiIiIABNzRaUENw0yju0VERMoghIB3ej2liIhI6VjgaEvaEdEYRyYiIiJDFszwHkek1rSIiEipWDjSdK7/0PukRUREysGC4ZsVdLCgSlpERKQkgiUtN6FTCEGVtIiISBmEAL45f4n3GjQmIiJSFo3ubr1bQ0REpHxcvZLWvWgREZFySdOaHowWEREpoxDAG2pFi4iIlE1K45504wfNl22IiIjIcIUQ8KYebxERkdJJm6O7g3MEHKqwRUREysHM8AaY1f8wC8NOk4iIiNB4wUYajBCMYJCqjhYRESkFM0ecpJCmjiR1JEEDx0RERMogCYZPUyMxo5ampJq7W0REpBRCgHglTUnTQBKMRJW0iIhIKQQz4iRJqSYBa9ybFhERkeEzC/hmxWyYBo6JiIiURC0EvDmPcxBMg8ZERERKw8A3pwK1YHobloiISFkE8GZGQK1oERGRUjGHDwFCeuRvERERKYFaavhgrj4lqCpoERGR0ggW8PVx3fX5u/VqaRERkXIIBj6oZhYRESkdC9TfTelco8tbFbaIiEgpJCFtvEDaNW9Iq5IWEREpAzOIzQwL9RvSzvlhp0lERESAtF5Jg5kRRR6nlrSIiEgphABx5BzBOaLIoe5uERGRcrAAsfcRUeQwDG96w4aIiEgZmBm EnsiH ExvFNLWkREpAzMIPaRwxsE5zQvqIiISEkEC8QVX39G2rsIgippERGRMkjNiOPIY2a44PQ2LBERkZIwc8QVX3 PdJLWsObrsERERGSo0gBxFAHmsYDa0SIiIiVhGN47h/PgHTiN7hYRESkFM4dvDug2R72mFhERkeEzw6dAAMx5DRwTEREpidSMOA2GA9LgSE0v2BARESkFM9yD51xsNN8lbXDnrd8ZdrJEREROeBMTY7gPffFeIw2kaUISUn7leY8YdrpEREROeI97zIXEtZqBBdIUgqYFFRERKYU0Nf5/lUgiHYiIccAAAAAASUVORK5CYII=[/IMG]

Copy and paste the output or use the advanced reply so you can upload the screenshot

Nevermind, you figured it out

Possible a blacklist involved ```
for f in /etc/modprobe.d/*; do echo $f; cat $f | grep b43; done
```

---

### Post by Ka Fish on 2015-12-18
[ATTACH=CONFIG]266236[/ATTACH] I believe I typed it correctly.

---

### Post by Hadaka on 2015-12-18
Hi,you must have made an error entering that command, it should look something like this..
```
hadaka:~$ for f in /etc/modprobe.d/*; do echo $f; cat $f | grep b43; done

/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/b43.conf
options b43 nohwcrypt=1
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
# replaced by b43 and ssb.
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/blacklist-watchdog.conf
/etc/modprobe.d/dkms.conf
/etc/modprobe.d/vmwgfx-fbdev.conf

```
Please try again.. You typed /[COLOR=#ff0000]**ect**
[/COLOR][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR]It is......../**etc**
```
**  for f in /etc/modprobe.d/*; do echo $f; cat $f | grep b43; done**  
```
Please try to copy and paste.

---

### Post by Ka Fish on 2015-12-18
My bad, that's my dyslexia kicking in. [ATTACH=CONFIG]266237[/ATTACH]

---

### Post by Hadaka on 2015-12-18
Hi,, let's try this another way. please do..
```
**ls /etc/modprobe.d/***
```
That is a lower case L ...LS...ls
thanks.

---

### Post by Ka Fish on 2015-12-18
[ATTACH=CONFIG]266238[/ATTACH]

---

### Post by Hadaka on 2015-12-18
Hi, you sent the same screen shot that you sent in post # 14
please try again...
```
**ls /etc/modprobe.d/***
```
thanks.

---

### Post by Ka Fish on 2015-12-18
[ATTACH=CONFIG]266239[/ATTACH]

---

### Post by Hadaka on 2015-12-18
Hi, you had a typo that time...you typed a  " [COLOR=#ff0000]**+**[/COLOR] " and it should have been a " *** **"
**shift/8 = ***

so, lets try again...
```
**ls /etc/modprobe.d/***
```
thanks.

---

### Post by Ka Fish on 2015-12-19
[ATTACH=CONFIG]266249[/ATTACH]

---

### Post by Hadaka on 2015-12-19
Thanks,after all that, the file we thought might be there..is not.
so, lets try this, please post the output of..
```
cat /etc/modules
```
then,remove the usb wifi device and power down the computer
then power it back up.
You said in your first post that you reloaded 14.04 and the wireless
was fine before the reload. Have you been without wireless since you
reloaded 14.04 two months ago??

---

### Post by Ka Fish on 2015-12-19
[ATTACH=CONFIG]266257[/ATTACH] It's a tower I built in 2007. The ethernet cable works. The wifi card is plugged into the motherboard. It's not usb. Do I need to remove it?

---

### Post by jeremy31 on 2015-12-19
Post the result of ```
lsmod; dkms status
```  Try highlighting lsmod with your mouse, right click select copy, then go in terminal and see if you can right click and paste, you should be able to do the same to paste the code in your reply

---

### Post by Hadaka on 2015-12-19
Thanks, again I ask, Have you been without wireless internet since you reloaded 14.04 two months ago?

and. Was the wireless working with that extra usb/card in the computer two months ago.

please answer both questions.

thanks.

---

### Post by Ka Fish on 2015-12-19
The wifi was fine with the upgrade from 12.10 to 14.04. The AMD Sempron Processor 3100+ maxed out & flash player dragged, so I wiped it. The wireless has not been working since the reinstall. It told me it needs drivers, but none I've installed have worked.[ATTACH=CONFIG]266258[/ATTACH][ATTACH=CONFIG]266259[/ATTACH] I can copy from here, but can't past to the terminal. right clicking highlights everything to the right & above. It won't let me copy from a terminal, or at least won't past. I've even tried using the keyboard to copy & past. Nothing has worked yet.

---

### Post by jeremy31 on 2015-12-19
```
sudo apt-get remove broadcom-sta-dkms broadcom-sta-common
```

Reboot and see if wireless works.

Have you tried using keyboard shortcut CTRL + shift + c to copy from terminal and CTRL + shift + v to paste into terminal.  I know you can't cut/paste from X term but gnome-terminal has always worked for me

---

### Post by Ka Fish on 2015-12-19
Thanks. That enplanes it, I was using X trem. I have not found everything yet.[ATTACH=CONFIG]266262[/ATTACH]

---

### Post by jeremy31 on 2015-12-19
Should just be a reboot away from working wifi, CTRL + ALT + t should bring up gnome-terminal
If it doesn't post ```
ls /etc/modprobe.d/
```

---

### Post by Hadaka on 2015-12-19
Please install your b43 driver, From a working wired connection please do..

```
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
thanks

---

### Post by Ka Fish on 2015-12-19
It just popped up & was already connected. I turned off the ethernet, it worked. [ATTACH=CONFIG]266264[/ATTACH] I rebooted & now it's back to having only the ethernet connection.

---

### Post by Hadaka on 2015-12-19
please do..
```
sudo modprobe b43
echo "b43" | sudo tee -a /etc/modules
```
thanks

---

### Post by Ka Fish on 2015-12-19
[ATTACH=CONFIG]266266[/ATTACH]

---

### Post by jeremy31 on 2015-12-19
What does this show ```
ls /etc/modprobe.d/
```

---

### Post by Ka Fish on 2015-12-19
[ATTACH=CONFIG]266267[/ATTACH]

---

### Post by jeremy31 on 2015-12-19
```
sudo rm /etc/modprobe.d/broadcom-sta-*.conf
```

Reboot and it better work this time with the blacklist files deleted

---

### Post by Ka Fish on 2015-12-19
[ATTACH=CONFIG]266268[/ATTACH]

---

### Post by jeremy31 on 2015-12-19
Does it not work after a reboot?

---

### Post by Ka Fish on 2015-12-19
It is working now. Thanks to both of you!

---

