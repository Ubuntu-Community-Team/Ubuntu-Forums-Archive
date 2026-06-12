---
title: "Ubuntu Server cant Be Accessed Over IP or SHH But CloudFlare Tunnel Works Fine"
date: 2024-08-14
forum: Networking &amp; Wireless
---

### Post by rahulsharma49 on 2024-08-14
Hello All,

[COLOR=#32363A][FONT=-apple-system]I am having this strange issue, after running for sometime, my Ubuntu server cant be accessed over local IP, cant SSH, cant reach any service like radarr, Jellyfin or so, unless i restart it.[/FONT][/COLOR]
[COLOR=#32363A][FONT=-apple-system]But i am using Cloudflare tunnel so that if i am out of my home, so i can reach it, and it works fine even when i cant access services locally.[/FONT][/COLOR]
[COLOR=#32363A][FONT=-apple-system]Means I cant reach Jellyfin from local IP but I can reach it via Cloudflare tunnel and it works perfectly fine, same goes with other services.[/FONT][/COLOR]
[COLOR=#32363A][FONT=-apple-system]P.S. my server is over WiFi[/FONT][/COLOR]

---

### Post by currentshaft on 2024-08-14
<

---

### Post by rahulsharma49 on 2024-08-19
Hello,

Thanks for your reply

What more information you need?

Here is my /etc/netplan/50-cloud-init.yaml

network:
    version: 2
    ethernets:
        enp0s31f6:
            dhcp4: true
    wifis:
        wlp1s0:
            access-points:
                "MySSID":
                    password: "MyPassword"
            addresses:
            - 10.0.0.100/8
            nameservers:
                addresses: [8.8.8.8]
            routes:
            - to: default
              via: 10.0.0.1




My router IP is 10.0.0.1 and subnet mask on router is 255.255.0.0.

> [COLOR=#000000]What troubleshooting have you already performed to rule out Cloudflare or your local router?[/COLOR][COLOR=#000000]

I am clueless where to start and what to check[/COLOR]

---

### Post by TheFu on 2024-08-19
You need to edit that yaml file to ensure _forum code tags_ are used or it is useless for us to review.  YAML is space sensitive.

---

### Post by rahulsharma49 on 2024-08-21
Here you go,

```
network:    version: 2
    ethernets:
        enp0s31f6:
            dhcp4: true
    wifis:
        wlp1s0:
            access-points:
                "MySSID":
                    password: "MyPass"
            addresses:
            - 10.0.0.100/8
            nameservers:
                addresses: [8.8.8.8]
            routes:
            - to: default
              via: 10.0.0.1
```

Just asking, is addresses field with 10.0.0.100/8 correct?

---

### Post by TheFu on 2024-08-21
> **rahulsharma49 said:**
>  
Just asking, is addresses field with 10.0.0.100/8 correct?

Unlikely.  Most home subnets allow 256 hosts, so /24 would be correct.
The indentation of the wifi part looks wrong to me, but I don't use wifi except on laptops and never use netplan to configure it. Sorry.

YAML is extremely indentation sensitive, in addition to all the other picky things about it.
[https://netplan.readthedocs.io/en/stable/examples/](https://netplan.readthedocs.io/en/stable/examples/) has examples of a correct wifi config for different security levels.

Because I don't know your network at all, I can only guess that this is the example you want to follow:
```
network:
  version: 2
  renderer: networkd
  wifis:
    [COLOR="#FF0000"]wlp2s0b1[/COLOR]:
      dhcp4: no
      dhcp6: no
      addresses: [[COLOR="#FF0000"]192.168.0.21/24[/COLOR]]
      nameservers:
        addresses: [[COLOR="#FF0000"]192.168.0.1, 1.0.0.1[/COLOR]]
      access-points:
        "[COLOR="#FF0000"]network_ssid_name[/COLOR]":
          password: [COLOR="#FF0000"]"**********"[/COLOR]
      routes:
        - to: default
          via: [COLOR="#FF0000"]192.168.0.1[/COLOR]
```
The stuff in [COLOR="#FF0000"]red[/COLOR] is what I think you'll need to change, assuming WPA of some sort is used.

---

### Post by rahulsharma49 on 2024-08-21
tried the above yaml file and my server goes out of network, switced back to old yaml and now it is connected again

---

### Post by TheFu on 2024-08-21
> **rahulsharma49 said:**
> tried the above yaml file and my server goes out of network, switced back to old yaml and now it is connected again
[LIST]
[*]If you don't show your work, how can anyone help?
[*]Did you change all the red parts in the example?
[*]Did you do the 2 netplan commands for the YAML to be generated and applied?
[/LIST]

It broke, isn't very descriptive. We cannot read minds.

The subnet with that gateway aren't typical for  .... anyone.  That /8 subnet is something Google or China might use on their main, huge, gateway routers, not a small business or home user.  I suspect very few enterprises would have a /8 subnet either.  Typically, a medium-sized business would use a /20 netmask, but you need to know the "correct" answer. We can't tell you. Ask your network guys.

---

### Post by rahulsharma49 on 2024-08-22
sry for last reply, after couple of restart it is now working, i dont know how but it is working now.

```
If you don't show your work, how can anyone help?
```

What work i need to show, please tell

```
[COLOR=#000000] That /8 subnet is something Google or China might use on their main, huge, gateway routers, not a small business or home user[/COLOR]
```

[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA38AAAGACAYAAAAd7NtqAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAFGRSURBVHhe7d1/cBzVnff7r31NAF8wIWAx43F5I36YPBVDdlaOnIuBeopKENiLh92nyiFVJCyIspQHCnKrkt0/Yuyxcf54kvxB8sATyYUg/Kgb4ro3y4hYIEJR9QCmYsXaTox5Cpsf2rgYzyDZZJG55rJrrHvO6dM93TM9P/TLlqbfr6qB6T493ad7frg/OqdPLxgfH58QAAAAAEBTW2j/DwAAAABoYoQ/AAAAAIgBwh8AAAAAxADhDwAAAABigPAHAAAAADFA AMAAACAGCD8AQAAAEAMzPx9/g48Id8fSMkP/vHrcomdFe0NeeL7T8gbLTdVLqvX8cs35Kp/ KncscrOMz6Ql378E3HSP5AffCNi7fZ1la6SO356h/rvfKCPywuS scfyNdb7CwAAAAAmKYz1vL3we9ekDe cpVcNfqCvHDAzizzxi9VOLTPG6bD5E9/Kj8NPH7QMeoGTbsIAAAAAMTNGWr5c1vw8ut Kn/jfF ekDvkp98OtMuZdej2ujfkjWSwrIGWv8htl7Wmjb4kP/nxC2ptnkvkpmDZL0XSSRVK/6Smv Ju/42nVD31tMfO13TZC4k7JO08IS M6jnu i4ZLL3mko5gnW2rp50qrSs832/5LGvRDLaI6m3/S ImGR3UNu96o//UR MujtXWDfAAAAAMTWmWn5G31DnNGr5G9UgLkqrULPn/6lFIR8KbnpH26SS/70hDxRpWVwSmzwa1EBym0Z/IHc1PKBvPDLl0phcPQFcRI/cMu94FcItCj g65zuF4fqPAldp13fEWt78c6ENp1qOV1ubuPbsDzljXbLzwhP/md3rrXPVUHtmDwEzXfLv PKuj98ifykgmZrjcG83KTXdfXR9W6BltKy/9Di6oLrZ4AAABA3J2R8PeGbqX6yt 41 CtukmFrzfkBRN yrR8Xb7TccnUun8GvPGUen1LWq7SrV9qnTrEla4lvEQF0PJWxEsk/ZXSvKu rUNXoDVxla170Fdu8lvXTKBVS9zktfSZ5UflAxXY3O6ud4S2/3UVcsUPh0EfyEsD trHwPWK5piIvDAYWNo7llFW3aFC4Hy53hEAAADAbDkD4e8N Zc/XSI3dXhxxA1fHzhvBLphllzyje YcPjEUw3Gv9EX5Cff/758P/B44k9XyR2RXUHd8lIXydoN1P7DobCKMtKYnqaTlaVNv60xN 3cwj1AU1aFTyKjC 8cvAsupRs742THv7NqOtpgAAAADmrdMe/kzLl4o6ultkKMxUHfjFbRlruPtnxIAv4ZYvLxg9IaMdbrfMH3SUt/yFeaGv1J1ymi1p hq/UP1qr1Nf41exvH8dZDl1vP7RXeaOr3jBMdxNFAAAAED8nObw94G84XxgBj8Jhxl93Z0KKk6V9jS/eT4thZU3bgX9zbS6jtRg4aU8GtsxvApt99siWhtln4oEpLX7kWSanjMqqWnwrTXdVe0 j8aWrrAAAAANAcTm/4MwO9hK nc10iX1 nYlXkwC8ut/unCk0z0YI1mhd/NQf0ACn1g1EpgOkRR6d DeIl37jJ3N7iycA1jqZl8ceBAWd87nH5YPDJQMud3v737QAxEfQAMcFuqVWPOQAAAIA4mZ3wF3HdnQ43r qBXryBV8qZQVGqDPxi2O6fdmrKVt0hd3yldE2cuTWEHr1z1JE3IoOlu10Z9K7307eoqNNSWZO /jC4PhXknHTg9hRXyd/Y0UJNwFP1/YEe4MXvJlvjVhda f6ZkU251QMAAAAQdzN/nz8AAAAAwJxzBkb7BAAAAACcboQ/AAAAAIgBwh8AAAAAxADhDwAAAABigPAHAAAAADFA AMAAACAGCD8AQAAAEAMEP4AAAAAIAYIfwAAAAAQAwvGx8cn7POqTp06Jf/ 7/8u//Ef/yETE3UXBwAAAABMw4IFC Sss86Sz33uc7Jw4cy02dUNfzrwnTx5UpYsWSJnn322qQQAAAAAYPboRrdPP/1UVF6TRYsWmSA4XTUjpG7x08Fv6dKlcs455xD8AAAAAOA00NlLZzCdxXQm09lsumqGP93VU7f4EfoAAAAA4PTTWUxnMp3Npqtm NNdPnVXTwAAAADAmaEzmc5m01Uz/Ol prT6AQAAAMCZozPZTAy8OTPDxgAAAAAA5jTCHwAAAADEAOEPAAAAAGKA8AcAAAAAMUD4AwAAAIAYIPwBAAAAQAwQ/gAAAAAgBgh/AAAAABADhD8AAAAAiAHCHwAAAADEwILx8fEJ 7yCKpNUKmWnAMxFJ06ckEKhYL6vp06dsnMBNLuFCxfKkiVLJJlMyuLFi 1cAECzyufz5nd/Ogh/wDymg9/Bgwdl6dKlcu6555qTQQDxoP/Y88knn8jY2JhceeWVBEAAaHKEPyDm3n33XTn77LPlggsuMP9ftGiRLQHQ7E6ePCmffvqpfPTRR b/l112mS0BADQjwh8Qc47jyKWXXirnnXeeafVbsGCBLQHQ7CYmJkzr38cffyzvvfeepNNpWwIAaEYzEf7oIwbMY/rE75xzziH4ATGkv/P6u69/A7jeFwDQCMIfMM dddZZBD8gpvR3X/8GAADQCMIfAAAAAMQA4Q8AAAAAYoDwBwAAAAAxQPgDAAAAgBgg/AEAAABADMxu HN6pGvrgBTsZHWO9HR1RS r16HKehw77SvIwNYuye6usnbzuh61Zsuup/IRWKaKwu6sWbayDpXMsjX22dmptrmzgRUBAAAAwAyaEy1/hd05cdrSki7mJFclFzk99UNaXYmMZHt7pTfwyG4oquBZa92O5PpF0m1JcZ5tJMgC88moDP5wo/Ttt5O A9K3caNstI/Nz4/a VXs7/OX3bhxswyO2flVjD6/ObB8n9paI3Sd6q8bAAAA0eZA CuIM1SQ9Fe7ZU2bilp/iIhhCRUME470zEKLWXJ9RtJSlELRzijn7BUn0S6ZDe2SLA6JU7GcbbU0j6zk8na2pzgg2UAr414729BlWwdkQLcG6nK7f15Lo7fOgcA2p1oGVNLB717pe9tO vT87TJy58Oya9cu9dgirY r5SoCojU2KJt3jEjnI3pZ9djcKn331Ah0Kije 3irbDHr3iUP3zki2384qLZaiw5 22XQTgEAAGDyznz4KzoyVEzLmrSoAKj M6zCli0qWSGZ72YkOdzTUNfLmaTDaLI9LUkVQNsTBRkaDrb96eDXI8UNWbclcVu7FIPlJtzlJNFtWxq71SuGbZmnmJOhlH39prQJcNmh9lILZXdCcltty6TTI9n hHRPtgwo47a8qUDX2iEddp5v/3MqEHbIbTe32Bmr5JY7V8rgUHScO5Drk0M33iYdS 2Mq2 RzisGZW9kWFTB8teDsvLOW9RaXS03q9e /ao4VVr0DjyqWwdVGL2xQ1baeQAAAJi8Mx7 nP6cFNrWiIp9Kv1lJJNwJBd1HV9inXRtSM5M988AZ6daX6Jd0gk7I0iFt9xwUtrbkmoiKetuVeFM1dffvm4VVDXPrNfliq2jpzA8JIWE2iezc0q6W7rb7HOft37N7WKa e46Ndcyr6lyTFRZr0qU3upDapUBcp3b8nb3GjtdMpofEbliuXjRT2tJtYq8uDeiNW9U9OIrU6GlRS8eHRZH5f23RVrLll9 xSF5dV Vtr9Upzys6rojs9zOAAAAwFSc4fDnyF4VrjIbvIiSlHR7UgpDTuS1dcn1XSYcTrn7ZzEX6ILpPnqG09K9LRC2Akx4a8vIOi8YpnVIVXW2my8cKarAt0KCuTG5rDRVzKu9SCVD606o6aqKBd0BVXJby toy2049rqZhlpBa5UBZVpu7vBb3iK1pkLhT5LLa7a6hcOcDou1ll4py0NfAzcsVrNK1TW8dgAAAEzFGQ1/ZqCXsrCT7VeBqerAL0lZN53unxEDvlRvHdOtcKoualte3byRQWd34BcVhreV17FXsqZ1Ue2/LdMtiE6PrpN3bV tMgAAAABxdwbDnzvQS9K7Xs5/ZCWTUOElauAXze/ 2StDdtassF06/WvovEe3iop24BfTylc8LMF8ZVoDLdPKly EgqJpDawmkZSEWvpwA8kyvck7VuXXIdYuAxoykg8PwFJ4Xw7Zp1FG8uEum6P5WksfkvdDH0u36ygAAABm15kLf2agl D1bh732rrogV9cbvdPFapmsVXLhE/vWsQg073ShqryaxSLA9KrWwstM5JosBXT6Sl14YyUlkzFdY1uV07T0ll 78LgMaxVBkyCub7v7fdD4c9cB3jjmoiuom6XzUOh8OeGuY72qI6l vq 8rCorwNcKdetpnMnAADAbJr98BdxnZ2 CfrLeqCXagOt2GvrIgc5MWz3Tzs148xAL6oaevTRCva6RDPwi 5q2S2JfnuLha2HpT0w4IsOc93bMlI0XTDV49kVkqkY8CUsuT5rBngp3T6iR6S7V3SDozf4i19mRhLNutck1ioDJsOO1vmMf2 /A/Lc44eqhDmRVZlOWfniM6X779nRQtdcbadDWqTjmx1y6PHn/MFjRp9Xr73iOkl7o4UCAABgViwYHx fsM8rqDJJpVJ2CsBcMzw8LOl0WhYunOrfcdz758nmXdIZCmvhqtvPNh2eHd kHf0H2HyJZdnaWWQDPPX1o6H9nh3/pB31bi3teuk4d/VBq4xcxTgdLVEViXe /BV68NbM j7yd4z6tyXWDdAEROnToljuNIW1udvy4CAOa1fD4vS5YssVNTQ/gD5rHphz8A8x3hDwDiYSbCH2eMAAAAABADhD8AAAAAiAHCHwAAAADEAOEPAAAAAGKA8AcAAAAAMUD4AwAAAIAYIPwBAAAAQAwQ/oB5TN/fT9/jC0B86d8A7vUJAGgE/1oA85i 0efRo0dlYmLCzgEQJ/q7r38DpnvTXwBAPBD gHksmUxKoVCQsbEx eyzz xcAHGgv/P6u69/A/RvAQAA9SwYHx v2mSgyiSVStkpAHPRiRMnzMmf/r7SBRSID93VU7f46eC3ePFiOxcA0Kzy fy0e3oQ/gAAAABgjpuJ8Ee3TwAAAACIAcIfAAAAAMQA4Q8AAAAAYoDwBwAAAAAxQPgDAAAAgBgg/AEAAABADBD AAAAACAGCH8AAAAAEAOEPwAAAACIAcIfAAAAAMQA4Q8AAAAAYoDwBwAAAAAxQPgDAAAAgBgg/AEAAABADCwYHx fsM8rqDJJpVJ2CsBcdOLECSkUCub7eurUKTsXQLNbuHChLFmyRJLJpCxevNjOBQA0q3w b373p4PwB8xjOvgdPHhQli5dKueee645GQQQD/qPPZ988omMjY3JlVdeSQAEgCZH ANi7t1335Wzzz5bLrjgAvP/RYsW2RIAze7kyZPy6aefykcffWT f9lll9kSAEAzIvwBMec4jlx66aVy3nnnmVa/BQsW2BIAzW5iYsK0/n388cfy3nvvSTqdtiUAgGY0E GPPmLAPKZP/M455xyCHxBD juvv/v6N4DrfQEAjSD8AfPcWWedRfADYkp/9/VvAAAAjSD8AQAAAEAMEP4AAAAAIAYIfwAAAAAQA4Q/AAAAAIgBwh8AAAAAxMDsh7/igGS7uqQr8OhxbFkDCruz0rV1QAp2emYVZGBrjfrYuk 5fBKcnerY7JyBFQEAAABAhNkNfzocbR2S9m290ttrH9syUuzpkuzu2YlzMy8pxWezMlC0kz5HerbmZimUArPtgPRt3CgbvcejB x8a39fqcw Nj8/agvVqx8Nl23cuFkGx2xhhPDyfWrrAWODsjm0LvUI1qdOXSqElq9dL230 c2B5cvqBgAA0EQWjI PT9jnFVSZpFIpOzV5utUuO9Qu2W3rVIQqCc33A2JW1iXcct0K1iPd0rspbZdNSFqFLccGsHR3r3Sn3eemPN8umXxOcrY8uUHNW1/aolmm34tpScmYbelWv2zV1xhe3TYkZEgy4XKnR7r oOoy7IgE6mPqPuw N9rc/TDM kqBMbjN4D67LZK6bmm16m6170C04eFhSafT5kbPjdPBb7uM3Pmw7Li5RU2PyuAP75VXr/Wm3bC2t32XdF5tJsvo1VNbs6ZZWdU4te1/aRTnn4Rx1itqbC1r2vXRea/rnc52 7XO26lNFB8p5X5bpHdkjHUjWtg AOkS3V6lpWXl43YD7QN3h3HEfa2trsHABAM8rn87JkyRI7NTWz2vKXXKbSXFGFsrLejMn1WektC4Q1FR0ptqvXBFoOQ10th3Ny FbbsqhSWKG/12 p84Om1/LYnZDc1h4VJZOyToXAjKqiDpMVwS obY0khpxQK5/zB0fSX11jp1wmwOVVSPS3pWLbcI tq9tSmFDbMmUq1CX6sxFdRm3wS6kgSPDDbNi/VwalQ27zw1aLdHyzQw695qgYqI1KfmSlLK/2lRjLy8gVyxsMRwdk74ti1u9v7ebbpOPtV8WxLXKj UPSmqq2tjp1KXMg1yeHblTr18FPu/oW6bxiUPbut9MhKvT elBW3nmLHwzL6wYAANBMZrfbZ7pbshuS4qiw5l/zN5Xr9xIZ6fLCWWKdZNrc8OVT5RkvJaXXqMBUkMNmI47k kUy3w0ETVWn7jY1f1LdTtOyJjXktzzq9e4dVvPKkll6kwp1wVBr6lKNbtUrtRh6nJ0q OlWRq 1EJhpV3fKrrKWsNH8iH2mjcr76r v3uN1hSzrZlkwpXKv31WyVtfKVdK5q6zVTodH 9QLdyO/Lm0r3AW1Tl1C9LpEVoaCZIukWkUGh6I6c6p1vy1lwbNFll9xSF7dV6NbKQAAwDw16wO mFY 2xLWrXukFHNmkJRJXfOXSoZaCRNqWvKF iGyWJCiWiq3NRA 1SPULbNB6a8mZGjYbtHZK05b9WCnWxvdbekWRk9aMsEgHDW4i24lVHVLtqcbbxUFpu2APPf4oVLrnA5nbx S1s27VEjUjy3S vi9fujSQfHQ262yxZSpx ZW6bun/rV1nnDrnA5gh0Sufdhu62HpHNleCoB16hKlvBWxJbXSPotS3qrohkUAAIBmNOvhL8i0jNnukIX XCAYzSZ9jZ/dbuBRs5tnlPQaSdg6u10 K6OfF/qy/QnTqlfebdMPwrY7qFk2GIITGcluy4gEuq0Cs8u9/m/wxi2l1rmlHbJDBa1Sa90q6dzcIYcef04trbtG7lAhLNByeHWnbLnxkPTl6g VYq7/e7FDttztvdptGSxd79ciHd/rlJUvPuOGyTp1AQAAQONmMfy5t1GIbOFLrlCRrCiFRgNOWStfUU2XtwZGSiQl4XcBna60rGlzZK8T3eVT768zVDDXD9a9Vi tr dTAXRDUgrBawn1PplurQXJ/WK2bm8BeErBb5cfxqpILpda7We1W9dcfvCrN1DM0pTUbHyrU5eRfLhVUF9TWN0heT/0RXO7jgIAADSjWQx/SVl3q27hqxzUxOnPSaEt447uaQOa36WyOCC58m6ZwUFjHN01MimZDTXjleV1tQx2v3SkR3f9nEKzo27tM uq0eWzeMQ7k9Tht9Z23bAY1cUzvUmFR7XPvfPmdhiYd8ztFdwRP8uDn7n1wQ8HVQwKKLwvh8wgL3pk0Mrr7nTACl9rF S xoz4WR78zG0Zym/9oK8JbJXU0np1Ked22TwUCn9umOtoj4qb vq 8rCou6GulOtWV9sXAACA WvWB3zxRud0r4FzH7lUtnT7AxWjuk03UHud3C/EBLYQFRRXPGtfr9JTurt0W4h6dFdLPcCLDl7u9nsCt2ZISrrdXofXyA3W7QAuUV0 Tdj9ru6y6V3vl5XDt7qjibqD07j7WRr8xh3RM7r7qXdM6P6J2XBA u7pE/Fv9RDWsvo6Wfl2nzznj5Cplt8xaK8JbJH0tSvD3S5VgNMteqXRQ8MOPHqv9EnpVg8hV6 RDhmUZ/wwqYLiQ7pu7gictetSaVUm0GVU2/ c9L3dIWsibxNhRzkN7Mvo8 q1V1wnaW 0UAAAgCYyq/f5AzC7pnKfP3Mvu8ejukIGumSaX1ibfUyrKgGF7HSun07qunhO6VV7aeoI7N3rV8tvupmauUd0OtVZeo /iZed7aatTNnVW2Lw10SwXmGO7zBwDxMBP3 SP8AfPY1G7yDqCZEP4AIB7m/E3eAQAAAABzA EPAAAAAGKA8AcAAAAAMUD4AwAAAIAYIPwBAAAAQAwQ/gAAAAAgBgh/AAAAABADhD9gHtP399P3 AIQX/o3gHt9AgAawb8WwDymb/R59OhRmZiYsHMAxIn 7uvfgOne9BcAEA EP2AeSyaTUigUZGxsTD777DM7F0Ac6O 8/u7r3wD9WwAAQD0LxsfHqzYZqDJJpVJ2CsBcdOLECXPyp7 vdAEF4kN39dQtfjr4LV682M4FADSrfD4/7Z4ehD8AAAAAmONmIvzR7RMAAAAAYoDwBwAAAAAxQPgDAAAAgBgg/AEAAABADBD AAAAACAGCH8AAAAAEAOEPwAAAACIAcIfAAAAAMQA4Q8AAAAAYoDwBwAAAAAxQPgDAAAAgBgg/AEAAABADBD AAAAACAGCH8AAAAAEAOEPwAAAACIAcIfAAAAAMQA4Q8AAAAAYoDwBwAAAAAxQPgDAAAAgBgg/AEAAABADBD AAAAACAGCH8AAAAAEAOEPwAAAACIgQXj4 MT9nkFVSapVMpOAZhrHt8n8k 7Rcb XzujhqX/u8h/Wy9y52o7AwAAAPNGPp XJUuW2KmpoeUPmMcaDX6aXk4vDwAAgHia3ZY/p0e6ehw7EZDISHbbOknaSbPcsyvC84yCDGzNylB7VrLrgyWO9HT1qP WpLt7pTttJyLKPeHlyrnbyxXtpNbWLb2bqr4AOKMW/KN9UsVZ/5vIi3eL/Ph/ijz/ljtv4sfu/6Mdk9x9HfLg63ayzO2P7pPv/bWdmLL98tDqu0SqrWs0J/eve1luGPiZZFrsvDPuqOz51W/k8F/9vXzrmovdWW/9Vna csQ8PX9VYL7xlvx2pyMX/t23ZO1S9erXfyW/ fMK ftvrZXgUp63BnbKK3K9bFr3JTunUXo7r4ipxflfrrr 6Qvvj4ztkV/982FZ4U3PoKkfizKhOrrHSa7fJH87rdXWWc80j8tk9t18pv4tbZedqf2bLWWfn1nlflf/kp6rx2LyZuc7YefNFPN7qD Cfyu6lubzeeC4WxY0g79Ts/e7OlfM3vcmeGzqHcfGNd93by6aHy1/Ouj19kpv4NGdykl264CKWlOgg6IKdqJCnL/ObRkp9nRJdndwjUnJbAssE1guKo8Gg2bpNVnJ5NX2plpX4Azb V9E/vNlIk98U2TxWXZmA3TI27ev8jH94Nc83nrviAl9mzZtKgt k/eldZumdoLy1jtyRJ9MqTpsmrXgF2HpWvnWptk5kZ/ysajpS/K36hhxQoL5aMa E7P4vY20XIUL/dsUeFx/wZvym1/tUTEBc8XF13zr9P77gTNu9lv GmnRa7jlz23R08GvovXOtDLqom5Jm VysmJbVtYlbLnl7OySXKq8JVEpDqhAOiTt5a JmF/YrV7f78VBHTK9Mr3dvbJiQ1Fyuvzi/yRLj/6bXBNaZ1ndTL1LaTTYMqm30yvtkujPmVbM2q2WiKNaLX//9f8QeeTvRD47JXLt/xD5/WF3fiMtfyN31Q56 3WvqIC0bn9QnrbzQq2CpvXuQdljJ0XWygN S55t fvO7fL0k/bV1zwggz/PyEX6eUXLn7u8tx35zmOy776r7cTpEmz5E/P8Tf P2sv8v3a73FYYt01QlV6/Sb72of7L6vlqySNyxL4u2FoY/gt1 PXmBCrixK/8L t6O5e/V/aX7orWL0cuXHW vHnAr1247mb5N8Vbq1vHoxX787cXlbcghOsc3De3hWqFfPmjN/1jVtlSWjKVY Exr33ffX7 8mUi7x PbvmL3E vPu57XXp/g V2PWrdR963tQq2ZFS0rNSpf6gey2TZcvX5aKClIvTem 1fJL8vr1fF57Jsv2q0wOj1/05WyPkH3jR1N5WlH4Mxdcf9nxVcyypjXBrZtfK3 Z6sem2vaDwnU5X75sjnl4H0vvW9m B98H8x78RdLXi7xiW/LD71Od9zCk1mdHqfW5q1EW/k6Et7Fs1Zfl IEGv Ohz2edZbVA7wb9efmyCm5vVvt8RrX8 S3TAd7xDn02PXWOX i9UL ny0WOfBRosQodw7Lvky57SWSF3gf9G2Hfx jPkTs11bKK/Sj7rgV/pyqOuS/8uav2vQkfn0rVthX8TJl9Cbb8Bd93Jfj9069zPv9l/7upueXhffbqVfs4YSrm8TV/SUm3J6WQD/avbICzV4WgtKyJCkDpbuk1wW KEklJqLCZ6y9rFkysk2xvWfAbai 1ZnYnJLc12MXUkVw 45b96JtyTaIgQ8OBdkO9D4l2SfvBTwdWuy7TMpmVgcBhKfQPqaDolhP8UMvnz7VPlGu/KPLfb3Wf/5/PlYLfTNqz/WVpHXBbBAe3rJWn735IxTTFBr9Wv/VwUB64Zo88uCOnomXJ00 KPGZbFB 7/EHpuC9c7ip1EfXX9c5dcn9/5ZKnz8Wy9lub5Hp14qH/gdtU8Q 3bmW6Xv0zq/ hC5y0Hlf/VKbtX8CvX6ZO2H4ne8ZsmU//A/qKHDfr1cv vQpNr8ivXq/8O7n5a61ajzmxUMuWnxxHOy5v/vlCt6VQr/v8I/LKgO0PrE8q1InT eofcnfb16t/4H8jv32ryv743JORUp3d14Xq/P6bpitQ7X0v1/ix0MzJzEfusdDLrvjoiH8iHVZtP3WZPYG5QJ0UmbJN8vfq5Li8vkfUydT1trx6S4Z7XNSCdl1l9bcnqn49VPjQ622Efu91vcwJbOCk8shH1d5bd7/0Hy 8/TL19ssr6UBxoXq/9bL6PXdP4s739/vvVx2XV3b Vu1lPVGfnzrHRinffog6OQ3WZdP1KsD8s66L/m7qfXdPSN2T4vL31N3WztC q2PlBI6dXz6Zz2C9z06tz12tsrC3BtQ2pPQ5v/DPpcDoqvUdL1djWf35VAFAH0dTp/Rf3NA0axo4fsHfmb9bIcffD x5I9 n42/K4c/b1wdDj91e6XOkVP2M1Smr813T2yz9TtnvUeTvR/XvTc3f2oDGtxXgh3j3NZv 7sty/JVfhX7/gt9N/R4deaXKd6/mccKZdMYGfEkuU knXyh1pyzmJNvVJV2hR/j6u8IRNZFYoULaFKmw1TOclPa2slY/Iy3dKnwlh1UgC2w/GMRMsOsXyXw30EKpQmd3m5of6HKa/qqX0mzIHXL8/XT 4EiyPa1KCjLwrIqy3YHAqoJm1wYJB1AvKAI13PVVkXf SeRq9cFMLhH5zR3qy71A5P9SH6X/Xmp a9jTd6 W1avLHzbceb7T6V Td9HXbpC1MiIjo2qiJSM/U0Gt1HJ4kVz79bX2ecntj35PvPa7q297QNa /rK8pl8fcKy/T57 zmOhdWU2PyCy/alwXeYDFdK 5p3Efuly9Y/6cflL3QzrBs1af9mdrGVpLyxcLFf lfqX qNj5mTg6OuO6ULq19GcfESFvTDvdd/w66heZwLe70v/yE9p38vVOhZvyTvqRC 4b2u//mV12tSI4H662wi2Vlx8xYqK9Sy7vhT4v/RVtZ3jh VgWZg1x0WFs9Lxc sk9rgcffuwHA8dl781f1CYjmrvrbz1exMYSu R2tw6dWL5vlM9hJ /Qq70/0L/lvz wPHQfl98zTdMWHCqnHjWUu/YGKHt16GOXeUfYSy978eXyfX e2o/G6F9VyfY6jfK/ ykdavxO6W6 NzPR/Rn0C2r99kpqfX9qlamP cRdS1T9XMQoervgf58Bt jL33NnNhPjwpGL6mwuvzyiPeqzvHTXdzVL0faO/ZL18o39B9ArMa T fLiiu8905/piVwLBXzmiqf6VqfsWDZJL9rk ly2dBvrc9 Z/33t5FtqffH0YE/sJ/mOIu8 YfAFpan/dY79z06Lseq/Y4E1TqGOK3mzmifEdcGmmvuphx8CpLbGgyS6tGjw1awC2YZ08pnt22a2ew6vGv igUpRqy3Z1gXRku2tUuyOCSOCZGO7PXDZ1EOq3lOT3hdpe6kQGMWqW/xfdeqWLRY5H92i7z2X93bOvxJfZTu/r/tQpMUfc1fKaw1Zr88ZINjx/byBLpWWoPnLC2t0ip7ZKTU08TI/6t63ZN3hUNoqDtps3FP5o4f I3s3LlTdp7Ga2OO/ttxkQsuaugkJCjydRddWOOkt1GTOBZjx9Tpx/lyoek3bC29qEodviRfM3 tVuvU663SKqJbEk35P5e3rERtpzLMmuPy/ivuOrxHYF1Rx 3iz0//qEU5 qHa1vE35TfBuuwMdGWsJ r4qppfdIF9Okn1jk1dJogckVfsa6NayDxm38 /MPz5rPhsnC8XBYOm fzqE9qpfR jPzu1PneNfSa996GyrjNPv0fnfz706Zz8 13 Hu 0rZaBgBcl6vhFvY8Xf6G055P PpljeVze/Odg/QJdJGt9xmqU1fuuXXxNWpb55eEWtXqi9rHq x/5na3nqPxFbcL/HNpHqdvmJE3ie4rT64yFP9OKl0qWWtAaYFoLi4dVbGpExIAv6tFw10nTjVS/plvSxZzk/Ma46PVWXEPoSaSl3ev6Gezyaenr MrXxeiimIyTp0S sVPkf33gdv289Asi4/ fSOaXIp/8h13otPJC310ysmXQBEfdLXTK9DV 0w6i84j56 gm093mfO8kodrJYLObpWNh/gKu16u7zdoTVK/rlHfi6XeX0ts2JVOgu2XqdYQeZ gv3 eXun VHmfw ptpHRvbSqReo1t33JPVyZ1IN2wSn8F6n51an7taZfNW1Htco VpRr97DXG7VJbX0W3ZrfUZq/P5q/ldc1t13W62XvicW10h/a6 wUedwB7tNH5PMSlnKPwVxBkqSDI1yWa99BozmMvessvyDD0wS0U3zcbpa/miR/VMyAqdOY oEntd4OFJNc6Vun4O F0 tcB6gWnS9/D7zz0i7xwTOTUh8l eEvnzX2zh6fbHl VpPYCLCmk/21Dtz45lrXyjIzJS3hqopL6oQuM7IxHXAsaAGZlP/cNpTgajuqDNLPNX8hrdw6qJfN2xv/h/sZ8R9Y5FVOub ct3HfbE3lxb9OeDah9stzp9Qlj1JDVqO5V/Ya93PKPKzV/2Z4FpITn l0m/t77I1s2jcuwj 3SSpvpZi2JGwrQn0offrlxj5L5XfDbKuq2Zz29ZC1vd72Mjnx2r4nMXUKvMvg VdZ15 j06/m/BrU/9/W5M7eMX9T6aVjZr0t nKi32UWp9xsrLGv uecFIX9d3RN5p4Ac 8ntT7f2fxP6VXCwX6up/WL/2k1Xve4rT64yEP2dnVnKSka5qrWVVpaW7W8W/8ts1mBE5c1Joy1Tv0llHcn3GtPBld5YlSycnuWJaMqau6v8bkmr74QFeenTXz6hAarldP9V6hlXkW btc1LW3ZqWQn9vILDq0U3Lb1kBNEYHwOv h8im/0fkpbftzDPl9RHJ26fyx4ciun2KPP2YN8DLMcnteFD2BK4h9Fy0oVNuf/1B2R4Y4OVY//2yOnJwmGagBwsI/8Vf31JCIq RqWRODgInpm/9ofGudF53pN/7JyGVdYnive53/nJvyW9f0bfB No0W7gmcyxstznH65Znry0yz8vpQROCXZCOysE/q1P9v7rSnnAGT5jcgTjK11OxneWla2A8lcdFLf36r/yugxXH 63fBkblm2Fe96tgi5Ue2KHhFgevW2Jp aOv/85cS deg WeNB55z98Zc71RNfWOTV3ldR87KIePB6/nCqjY96j37HjgmiZV7nif38l8BrVan51an7t6n0nPl Ty5aquLwU f6qus8Fcy/X K6U6mWsn7fNZU P42ffRvx5vbI/8LvAZm/z3qfIzHXqPan3GapXV a5VfM7ttYyXN/BjObnf2vLfRKW83hVUIDXdnIMDXFV BxpW6zjhjDozN3kvv3G6Xm4yN3n3wp6d1Cpv8h59q4fa3O2FbvJefkN6Rd8uInidX2nbertRt6Lw1qvCa9mIpOHbRqhIuKG0r/7IohXHBXC1bFO/pyr0NUpfCzi61U5Eqn2Td 82C/pWD3dJ4JYLZbdnMOVPukXmNg53jUjH3SP2dg 6W2iftG5plQe3N3Crh/LbRgSXPW30P4Dhm7zrLkrO56sPs63L9cmHHhH0G/K7spvo6pOM0tD4ZtngkOTBkx7dhahaS4L x1WPUuiXu/X0h4G/Xo9f790kOLxNTZ IhOpVvm3dbct29wnuz7euOKiWm8StHmrse7kpHwvFq6NWOQR YJv6uAWGMg/uZ7hMt0Sk5S//7I6w5972omx4/GCdTH0Dx6Ve/YPlqiw0lL6ph65yla6Q/mv18O2Xyzv13tuy90gdoarrrnyty8z3T7jLXh/aV1VmPnqlz2bo86M/GzWOTbXtBwXfa80dbt597tfTf1/D34vQ 23qcVjO193SvNEjK8prvIdBNT876hUNf 6UQFnoO1H HTefc /WCXW 43ZfI78T5cvqGcE62c nHi0z8jev7PNq1hV1q4da6h2/0Gd4mXx5lR6tNFDf4HtV/n0K7btewFXrczTVsnA9teB3peyzaPYzXKcgbzul39TwuoO/tVHC9Sxty8y3x6b8ffe/P1ZwG8HXGWXH1X t/fxWP06V/6aiMTNxq4fZDX8AZtXj 0T abf6/W0gAOrg99/Wi9y52s4AMKe9NfBbkXXRAQ0zpEoomDdM/avdN29m6RP5Wn/wAjD75vF9/gDMBB3kdEuevnF7vYdejuAHzBPqpN6Rxrr7Ii50q0941ETTtbvBbuGToVtwQt0T9efxfbrsAc2Alj8AABBP863lr1bX0Rk1ue6JAE4Pun0CAAAAQAzQ7RMAAAAA0BDCHwAAAADEAOEPAAAAAGKA8AcAAAAAMUD4AwAAAIAYIPwBAAAAQAwQ/gAAAAAgBgh/AAAAABADhD8AAAAAiAHCHwAAAADEAOEPAAAAAGKA8AcAAAAAMUD4AwAAAIAYIPwBAAAAQAwQ/gAAAAAgBgh/AAAAABADhD8AAAAAiAHCHwAAAADEAOEPAAAAAGKA8AcAAAAAMUD4AwAAAIAYIPwBAAAAQAwQ/gAAAAAgBgh/AAAAABADhD8AAAAAiAHCHwAAAADEAOEPAAAAAGJgwfj4 IR9XkGVSSqVslMAMD0nTpyQQqFgfltOnTpl5zaHhQsXypIlSySZTMrixYvtXAAAgJmRz fNucZ0EP4AnBY6 B08eFBaWlrk3HPPlQULFtiS5jAxMSGffPKJjI6OypVXXkkABAAAM4rwB2DeePfdd03o 8IXviCLFi0yLWXNRLdknjx5Uj788EMTAi 77DJbAgAAMH0zEf645g/AaaH/mHThhRfK2Wef7Ye/ZnrofdL7pvdR7ysAAMBcQ/gDcFrolrHPfe5zTdfdM0jvm97HZrueEQAANAfCH4DTppmDnycO wgAAOYnwh8AAAAAxADhDwAAAABigPAHAAAAADFA AMAAACAGCD8AQAAAEAMzH74Kw5ItqtLugKPHseWGY70dGVloGgnp6CwOytdO0MrDSjIwNYuye4u2Gm9vXB9ousVwekxy5XWVYu7narrNMdlevsNAAAAAI2a3fCnA87WIWnf1iu9vfaxLSPFnkYD1GxJSiZYp0C9qgdAFSKfdSTdlpZCf05FO2CuOSa5 1bLQ3 0k7798tDq1bLaPu7vP2bnV/HHh/xlV6X3Kjdn4Vx/rvDyz/kNradB2Qvo2bZXDMTnr298nGjRvtI6IcAAAANc1q CsMD0kh0S7phJ2hJdZJ14akFIYcFad061iP m9BclsDwcu2sJUeehmXbuXL7h7wW 8eelRN96sgOaxes3VArWmKVL0ybSqvHqmyhqIjQ8W0rNm0RtKqNnsj0p9pgfTqvHOvnVvi7PT2R4Xf/sN2ruYehwHv9d5 lB2HyhbTUlm45bNWGZqTDn4d8uDrdtKn598lI1sGZdferxmLRu74gIiNZoTu6/e0QeGNDLqsejrfLguhqBTgXFju2t8phZ9z4Z3DIid92XU1udKh38tsugnfKNDcrmHSPS cgu2bVLPTa3St89fWppAAAANGpWw19ymUp9xZzkyrJHcn1Weretk6SKUd293eq/bktcd1oV6sDTUwy0zOlyFWYCAabQPyQrbPn37lbhT4VJaeu265wdJsi26eCnAqAKic4fwjtlQml/Qu2PW69uVedQHFPBryefkawpz0p7XkfeIEdyqtxthVT7YY6D OtzWya9bqK6K2uPFDeo42jXl8n32NbUWmVoRm7Lmwp l98ut9t5vj8 pQLh7dK54SI742r59pa18vQr0XFu/zMPyp7vdEqmxc7462/LA9c8LS9HhkUVLB97WtZu bZaq uiDZ1ysvy2t1WgujHHhUt htl5EbO2Slnec5kOuTQzfeJh1L7Yyrb5HOKwZl7/SbGQEAAGJjdrt9prtNMHN6Aq1Q9Vrn1Gt0YFnntxa6YSukvDVxJqiw1TOclPa2qPiogll/QdJf1elU1WhDRpLDucD1egVxhgqSVPPdJdQym3Ro9Tiyd1jNu9ULp0lZ9121DvO8xFu/CXC6i2l3YB2mxVRUPaJa8dT6VBjOro qe60yNIcb3Ja3 26w0yXHDo IXNMqKTutXbSiVeTJlyNa847JyDsia78YWlpaL5cqYTEvI6 LtK7wgqWWktZr9sjLv59C21 qUx7etUt2ZJbbGZ5RyavdWJnyEqnWIim1G4NDtP0BAAA0atYHfDGtfLb1qluHuGLODABTtyUqMFBMjwpOM8vtZuoHUv3o0WErGDoDnL3iJDKS8ZJYIi3tiYIMDXv7UJTDKggmlgUDVkJWeOsqFtQSSVkRKk6qJapx1xcKzephurcaKtDdqq89LOsmatQqQzO6aEPGb3mLdHmrinABy1plrX0aJRzmVCb7Yq2l10rrMvvUcMPiVKy6uUNFuupaQ FPxb9UefsgAAAAapn18BeU3mS7MHbXGDTFC31bc5LoDoTGGRUx4IveTqmpLsBthfNCqxvEspJT4Wy2B35J2/0PPTbZSpoWUjW9LSNJr25e19haZQAAAABiaRbDn772rEoLX3KFil9FKfjdJkvca vc8BIdxk4zM9BL9OigSd2d02Qqt5UvPFiM23pnmFa ghwOFevWwGqi1ldFYp17HaE WMN7w2G0Vhni452R8AAsR0Zkj30aZeRwuMtm/l9rLb1HRo7Yp4bbdXQ2jOTDFxKO5g/ZZwAAAGjELIa/UvfD8tsnOP05FfAy0V0stXzB76qoB1KZ W6fjYscsVSzo4O6A794 1pqCXR2lkYoFUlLRl/7 KzXBVMF41 oY2CeR/HW1xu6rrAUpiuDtamHGZCmVhnixlzf9/qI5O20Zq4D/M4NEV1F3S6be/41tLQJc7dfH9WxVF/fVx4W9XWAa WGr4W7jk6Pe33foVD4c68D7GhfZacBAABQz6wP OLdP8 7bk0/cqlsqfuiiiRr2txr8HRgSa7vkoyUulhm9QiZejTPGi1XybZ2SepbPQRuCTEz3IFeku16PNJKZoAWb AXM7hN0b/FQi5VGvxF09c dqe8/crK4fbKAV9CzPokcG1iVobas3bgFhUOv5sR8a7rUw8zkqg5prXKEDt2tM4 /95 Wp7XuqhDmRq297QNY 2Ve6t58dLfSGv7bTIRdJ5q7bZc/2p/zBY47198nT19wg19a6eG8KVmU6ZeWLz5Tu7bf/Oel7u0PW1LzYEQAAAEELxsfHJ zzCqpMUqngyH8A5i59M/e7RB7dJ98LhTV3/tN2au2WQfmZd sHfUP3u0Ue2/e9UkugmecvLQ8M/My/9YO rUTHSzfI4M8z/iAyZp4KlK7bA ty7z348tfd7Q0PD0s6nZaFC v8zUnf0eV W6R3aUbu2g6Zu87/DuALhSOsvL54hTp06J4zjS1jbjFysDAIAYy fzsmTJEjs1NYQ/AKdFw FvniP8AQCA2TAT4a 5z8IAAAAAAAbhDwAAAABigPAHAAAAADFA AMAAACAGCD8AQAAAEAMEP4AAAAAIAYIfwAAAAAQA4Q/AKeFvr fvgdes9P72Oz3MgQAAPMTZygATgt9U9IPP/zQTjUvvY/TvQErAADAbCD8ATgtksmk5PN5GR0dlc88zObR56n/S 6X3U woAADDXLBgfH5 wzyuoMkmlUnYKAKbnxIkTUigUzG9Ls3UB1V09dYufDn6LFy 2cwEAAGaG/gPzdHsXEf4AAAAAYI6bifBHt08AAAAAiAHCHwAAAADEAOEPAAAAAGKA8AcAAAAAMUD4AwAAAIAYIPwBAAAAQAwQ/gAAAAAgBgh/AAAAABADhD8AAAAAiAHCHwAAAADEAOEPAAAAAGKA8AcAAAAAMUD4AwAAAIAYIPwBAAAAQAwsGB8fn7DPK6gySaVSdgoApufEiRNSKBTMb8upU6fs3OawcOFCWbJkiSSTSVm8eLGdCwAAMDPy bw515gOwh A00IHv4MHD0pLS4uce 65smDBAlvSHCYmJuSTTz6R0dFRufLKKwmAAABgRhH AMwb7777rgl9X/jCF2TRokWmpayZ6JbMkydPyocffmhC4GWXXWZLAAAApm8mwh/X/AE4LfQfky688EI5yz/fDXTA 9T3rf9D7qfQUAAJhrCH8ATgvdMva5z32u6bp7Bul90/vYbNczAgCA5kD4A3DaNHPw88RhHwEAwPxE AMAAACAGCD8AQAAAEAMEP4AAAAAIAYIfwAAAAAQA4Q/AAAAAIiB2b3Ju9MjXT2OnSiTyEh22zpJ2snGOdLT1SPS3SvdaTsroLA7K9mhdn/dZrq/4BYG1d1 QQa2ZiVXTKtNdUvEpkKcnV3SI93Suylqydp1BuJgeHhY0um0uSdeM9O3eXAcR9ra2uwcAACA6ZsfN3nXIau3V3rLH1MKflPUpkJZ2fa7UznJbh1QEa8KJyc5FfnSCUdyu6suBcwhxyR332p56I920rdfHlq9Wlbbx/39x z8Kv74kL/s6tX3S27Uzq/iWP/9geUfUluborFB2bxxo2y0j83Phzd84NFSmfvYLINjtlDb31e9DAAAAHOg22dxQLJdPTKwOytdXV3uoyyU6dY7v2znXjt3etIbMpIsHpainS7n/MGRZHtGMu1JKQw5lSHR1NvWSdW/vFa16mxaCXd7r8/KgKmEbmn01qceZcdAv8YvU9sLtqfWKkNc6ODXIQbid9ev5dMrJlUPbt26cej0nr9o6IgGiN5uT u0fkgQG9rHo82ioPrqsR6FRQ7NjeKo Zde TwS0jctd9ObXVSdLB754 ad28S3bt0o8t0vr4vdLnb/iA7H2xQ7aYMu xQzqW2mL9 h0j0vmILdvcKn1qfQdsMQAAAObMNX O5PIZ2yrXLeliTnpta5vbbTMh3V6LnVp29sONI3uHk9LelpRkW7sKiUPiBFOiDn5bc5Loti2J3eoVw7ZMaaTOTv9hyZjyrKxLuF1Mh9qz7vr0a3TL5E73VXp9Per4eC2o2Q1F6bHhsFYZ4sFteVPB7/Lb5XY7z/fHp1QgvF06N1xkZ1wt396yVp5 JTrO7X/mQdnznU7JtNgZf/1teeCap XlyLCoguVjT8vaLd9Wa3VdtKFTbn/9ZXmtTmthudF9r8qhKzrlFm9FskpuuXOlDA7Z DaWl5ErlotXrXIHcn1y6MbbSmHw6luk84pB2TvlZkgAAIDmM/vhTwW5UgtZ6ZENdaVMSmaDdzFcWta0qVCT12mrIM5QQZIbMv41d lN9a /q0 FrV/kpNC2JnJdhd05cRLtkk6oicQ6ybQVJNdfim F4SEpJDKS8SvVLd3 5T0N1jm4bdPFNCNd60sdYc1rhnO2VTAsuV6FxCrdZmuVoVnd4La83XeDnS45dnhE5JpWCV65e9GKVpEnX45ozTsmIIrP1iaGlpvVyqhEUVyF4XaV3hBUstJa3X7JGXfz 5tr Wm3fIrh91hMLdaP6QfaYU3lf/eVXujezWOSp5tZsrU8FXt0hK7aYfHgEAAHDmrvnLBoJOdUU5rMJPYllw2YSs0KFsMoZ7ysJn1oStbOTgLG54S99aClDpr6rlhvf6rXfFvAquqWQoYCXUtGvydS4cUS oCMml7pvJ9SpI uVeN1FXrTLEw0UbMn7LW6TLW1WEC1jWKmvt0yjhMKc 6l stfRaaV1mnxpuWJy2sUF55sWV0plZZSZHVbo79HZrqdun6dYZvq6vNRT VPxLrbTPAAAAoM2Rbp zLGLAl6qtY7oVTgUopycQxMyIpbM88EtkSNZdQnWhHnHUnc4kCpIz1wZ64bBWGTAP2ev/5M77/G6cpmVwV6e4UVC5ulO23HhI nK07AEAADRqjoc/t8WseCQYutyWtdmiB3qJHB1Ud0W1A7 YVr58wTz3mNZAY/J1Ti7TL6gExJUtZt0/XR3Ugd2RtKeLXKEGvvjIQHYDkyInvs0ygjh8NdNvP/WmvpPTJyxD413K6jU YHv4dlx83VrvBzlbfsjeTDFxqGuo0CAABgroc/FWhuTUuhP e3ZDk7Z7NVSw/0Yrt5lnFHB3UHfvG6Wub8SvVIjz/gyxTqnM5IJuFIjx3gxdD3SLQteGbk0OAgLo7ugpqWNaqatcoAc33f6yOSt9OauQ7wOzdEdBV1u2zu dfQ0ibM3X59VMdSfX1feVjU1wGulRu Fu462hB9qwY74mc4 I3K4A8rb/2gw517nZ97fd hUPhzrwPsaPfbCgEAAGLvjA340vD1aeludwRL 7pcqjSQykwzA71UC06JtLTrbpVm4Je0dG/LSNHrGvrsCskE7 c86TrrVjs9wEvg2kRzT3h3oJjk i7JSOA49hQlo5evUwZ4o3X2 ff22y9Pbd9TJcyJXH3bA7L2yb7Svf3saKE3/LWdDrlIMnfdLnu2P UPHnOsv0 evuYGubZ2o10lc6uGQelQwa zomotkr52pRx6/LnSrRtUUNz YofcZkPiqkynrHzxmdI1gPufk763O2RNzYshAQAA4mXB Pj4hH1eQZVJKhUc Q/A3KVv5n6XyKP75HuhsObOf9pOrd0yKD/zbv2gb h t8hj 75Xagk08/yl5YGBn/m3ftC3leh46QYZ/HnGH0TGzFOB0nV7YF3uvQdf/rq7veHhYUmn07JwYeXfnPQN3Le/aCeCruiUh 0ooKPPb5Z7H/e6cq6UzkcC9/nTdMuhCpCuiPLT5NSpU I4jrS1Bf8iBAAAMD35fF6WLFlip6aG8AfgtKgV/poJ4Q8AAMyGmQh/zX0WBgAAAAAwCH8AAAAAEAOEPwAAAACIAcIfAAAAAMQA4Q8AAAAAYoDwBwAAAAAxQPgDAAAAgBgg/AE4LfT9/fQ98Jqd3sdmv5chAACYnzhDAXBa6JuSfvjhh3aqeel9nO4NWAEAAGYD4Q/AaZFMJiWfz8vo6Kh89tlndm7z0Puk903vo95XAACAuWbB Pj4hH1eQZVJKpWyUwAwPSdOnJBCoWB W5qtC6ju6qlb/HTwW7x4sZ0LAAAwM/QfmKfbu4jwBwAAAABz3EyEP7p9AgAAAEAMEP4AAAAAIAYIfwAAAAAQA4Q/AAAAAIgBwh8AAAAAxADhDwAAAABigPAHAAAAADFA AMAAACAGCD8AQAAAEAMEP4AAAAAIAYIfwAAAAAQA4Q/AAAAAIgBwh8AAAAAxADhDwAAAABiYMH4 PiEfV5BlUkqlbJTAOaiEydOSKFQMN/XU6dO2bkAmt3ChQtlyZIlkkwmZfHixXYuAKBZ5fN587s/HYQ/YB7Twe/gwYOydOlSOffcc83JIIB40H/s eSTT2RsbEyuvPJKAiAANDnCHxBz7777rpx99tlywQUXmP8vWrTIlgBodidPnpRPP/1UPvroI/P/yy67zJYAAJoR4Q IOcdx5NJLL5XzzjvPtPotWLDAlgBodhMTE6b17 OPP5b33ntP0um0LQEANKOZCH/0EQPmMX3id8455xD8gBjS33n93de/AVzvCwBoBOEPmOfOOussgh8QU/q7r38DAABoBOEPAAAAAGKA8AcAAAAAMUD4AwAAAIAYIPwBAAAAQAwQ/gAAAAAgBmb3Pn9Oj3T1OHYiKC3dvd3qv1PlSE9Xj/qvkshIdts6SZr5p09hd1ayQ 1Vth2oX0hSMtuysi5hJ73l2rqld1P4aESt39nZJT3DdkJrZN8r3oPyOmA Gx4eNvf20sO9A4gnfZsHfc/PtrY2OwcA0Izmx33 dEDp7ZXewCO7oVglHDXI2SuOt94zEPwao0NWeL97uxOS25qVgaJdxDPcI5EZOcAEP1EhMbC 7lROsrWOowl ooJ2eR3UuqZ88NFcRmXwhxulb7 drOuA9G3cLINjdrKO0ec3y8ZHD9ipeiZbFwAAAEzGGWkuSK7PSFqKUtAhqDgg2a0DMqDCTVeXeuy0qUQHFz1tH15Y0S1ipiWrqINP2Xx/ WDAclvXBrxyta39ulVt94CaH7HuyHVoej2lslzezp6MdLcKviK5XwxIwc7SITHdllS7WysMO7J3WL38q HWwfQm3Xqqyqq80PmDKmhbE25hVXXobrNlnirHWjOhUx0rfaz1fvf9XP3fe48sc9z8eQUZUOHSX5863v6 VnuvcYbosHWv9L1tJ vSwW 7DNqpenTwu/fxQ3aqnsnWBQAAAJM1N/qKqSA3lMq6LVO6 2N5i9W2jBR73DCWXK W61bL2JY//dTvIuktb1q3gmHKUWEtY9e1TpaqOYX IVlhW bqr8MNkMUNto7b2qU4XIpvk5Fsa5dk8bCKviUrNnRJJqG2UTUMJWRFQtXi2WBo1HT3Wbf URKppMhwrqKlMb1J7YPXzbTGsfY4/YclY8qz0nmdet3w3sCxLYgzVLDBVAe/rAy12 Ok66ZbJ4P7Vf5e44wwLXIbVdhq7ZAOO6 WA49uVMtvl5EbO2SlnVfV2KBs3rhRBb9W6bjRzqthsnUBAADA1JyR8OfsVKEq0S5p/7qzpLS3eZ03VYB41pF0d CawMQ66dItZv1R4UgFu36RzHcD3T9N65aav7sUlcpbzSS0/Trr0N1MVW0y622pqY /5OQkkirK2VZPX1LWfTcjyardP1X5NnU8bGtnVAtdFB2Uu9sKppun3xIXCpgNHutg62FaPw 0NhYdGSqmZY1ewMlJTjLS5R0nxbROhgJo8L3GmXOdbNm1S3bdvcZO15HqlIfV8jsyy 2M2q7brNa9q1MaW/sk6wIAAIApmf3wVxZYTGgZTkt31Wv1inJYBQWnJ/yabH VlrZiQUepcMBRj9DAKPXUWUfhiKpQYoUKbSXJZTM8YooNlNW7f7qtfF7rnD527jGq1V1Uhy/7mt6sZHSVVcA0 2ZeNMljbaigF g2WhgekoINh Y4VbzfteuHM6Pl5g5ZZZ83YpVavsU r2tph3RcbZ83YLJ1AQAAwNSckQFfehsY6TPdXf4a9ajaTTBicBX1yAZaoOqbiXU0wATNhCQjsmNyfb3un5YKiu4x1YEu3MJZnW49tPukQ2agC nkjrVaXreimq6fwS6fVuT7zeiiAAAAwJk2N675C3GvbyseaSTQKKYbZUEON7h4pDrrMK18ZdfpmVauKTAtZWWtiCWl7p 9Q3aWZgZkiWpBS0oypdaZj6qLO0BNVNfQ0v5M8lh7vK6fuwNdPpWo4wQAAABgbpiD4U8FoFvTUujvDVwn5o4gmY1s4UpLpqK7ZPXgE63OOtKZcAtbcUB6a3aNrEKFuGz5tYXlbPfPQjGwfrv9nuDImZqqR244qeoe1Urn7VP5qKXudX7JDXrE1ckea4/t tmfCwdZr57BlsuqwRUAAADA6TQHw5/i3RLBvwbPHUGyWhdMd2ATN6x515lJd/VRMKPUXoc74Eqi37tdxGFpV8GqtsprCN1V1u8C6Xb/tBOG22XTva9fYH2qHpka63NHRnXv61eqR1YO3xrozjrJY 3xunom23WE9LjHKW2vKzQPs8/1u/kCAAAAmF0LxsfHJ zzCqpMUqmUnQIw1wwPD0s6nZaFC6f6dxz33n2yeZd0 oO0RM2z9G0c7nlVrntkh3Toe6Zo /tk4w6RLbs6KwZu0beI2C5bZNfdpRJz/7/XrpOHf1Q iEyN7QKo6tSpU I4jrS1tdk5AIBmlM/nZcmSJXZqagh/wDw2/fAHYL4j/AFAPMxE OOMEQAAAABigPAHAAAAADFA AMAAACAGCD8AQAAAEAMEP4AAAAAIAYIfwAAAAAQA4Q/AAAAAIgBwh8wj n7l7fAGIL/0bwL0 AQCN4F8LYB7TN/o8evSoTExM2DkA4kR/9/VvwHRv gsAiAfCHzCPJZNJKRQKMjY2Jp999pmdCyAO9Hdef/f1b4D LQAAoJ4F4 PjVZsMVJmkUik7BWAuOnHihDn5099XuoAC8aG7euoWPx38Fi9ebOcCAJpVPp fdk8Pwh8AAAAAzHEzEf7o9gkAAAAAMUD4AwAAAIAYIPwBAAAAQAwQ/gAAAAAgBgh/AAAAABADhD8AAAAAiAHCHwAAAADEAOEPAAAAAGKA8AcAAAAAMUD4AwAAAIAYIPwBAAAAQAwQ/gAAAAAgBgh/AAAAABADhD8AAAAAiIEF4 PjE/Z5BVUmqVTKTgGYi06cOCGFQsF8X0 dOmXnAmh2CxculCVLlkgymZTFixfbuQCAZpXP583v/nQQ/oB5TAe/gwcPytKlS Xcc881J4MA4kH/seeTTz6RsbExufLKKwmAANDkCH9AzL377rty9tlnywUXXGD v2jRIlsCoNmdPHlSPv30U/noo4/M/y 77DJbAgBoRoQ/IOYcx5FLL71UzjvvPNPqt2DBAlsCoNlNTEyY1r PP/5Y3nvvPUmn07YEANCMZiL80UcMmMf0id8555xD8ANiSH/n9Xdf/wZwvS8AoBGEP2CeO usswh QEzp777 DQAAoBGEPwAAAACIAcIfAAAAAMQA4Q8AAAAAYoDwBwAAAAAxQPgDAAAAgBg4Tff5K8jA1qzkimnp7u2W0J2IigOS3Tok7duysi7hLnf41l7pPiO3K3KkpysnK0xd7KzJcHqkq8exEwGJjGS3rZOknfSWS3eX76e7/0PtWcmu95b2jp2d1Nq6pXdTrQM0lddgPhoeHjb39tLDvQOIJ32bB33Pz7a2NjsHANCM5s99/pyc5FTkSyccye0u2JlNSge93l7pDTy6UzkVcAdUJAtzenpU3KylFAZL68tKJq/CY8T6XFN5DeLngPRt3CgbvcejB z8KsYGZXNg c3Pj9qCaAceDax7Y5/aWi2TrAsAAACm5LSEP cPjiTbM5JpT0phyKkZWnRrldPTJVk/JOrWuC7p8h47S3GpsDurlhvwy3Wjm7NTv7Y0z5vv0y2NgbKurqwMmBYyvR0dxgqS2xp8TfXtNyq9SYUvFX97g8E34YbhnlrrKzoyVExKe5vfZqgkZd13M5IsDokTbNnzTOI1 vhVHgfNPRYDXvnWX8uv1TEpvScu91hP7X3CmTQqgz/cLoM3bpFdu3apx8PSObK9RqBT4eyePpE7H7bLb5HWxVvv22uMzo85tl 4sdssUsu0sevnNEtv9wUG01ymTrAgAAgKk6DeHPkb3DbhhJtrVXDy06oGxTISmhwlJ3r 326IYQUdPBFqxgCCn0D8mKbW6514UyOC 7IVlqYTNdTHOSCK4vocLeL3SLmNclNSkZ9Vp3XfW335ikpHXwzQd3fIVkdCAb7qkehhJJSegw2l 2QGKdZFVdIrumNvgaE8iG2kutlN0JFXqDLZGO5PIZt2zbN X6iuBeel n j7hTBmV998W6WhfZadbJH3tSjmUrxK4xvIyIivlutUtdsYqWXOjyEiV5Ufzh0RuXKOWcrWsvk5Wvv1 1fA3qboAAABgymY9/BV258RJtEtahw4VQDJtEcGkCvPatu5AWHBbsKRfzbdzxFt3UFvGDzkmcEpRCjp3mQAUDB9uKKumoe03KLlMVShfCIQnRdWnKxhOK6hAus0NiH6LWqiFLkojr1HBrl9U Axch5hW 9kW7pab/moppVUEd2ev/75O X3CGdIiy68QGRzyuleOivPaIVmZ8sJdmaUpaZVD8uo L5AdkL0virRWWb4ltVLkxb1 V8/Rfa/KoSuWq61GmWRdAAAAMGWzHP4K4gwVJH1rKWSYQDGsgoOdrqWowpKEQox6bM2FA9SUlLooZvurr232tl SXN8lmVrdP21gdVvndLpyu6XWvH6v3muKBR2H3XmBfesZ1oVVJNLSnijI0LC7Vbcrr24nPT3HCTOpRTp tEu2yHZ7nd298v43d8mOm6sFrlXSuethue61e 3yz8jyR3ZJ59W2uEzLzTtk12aR7fYavnvzt8muH3VUDX TqwsAAACmanbDnx7opaj 1xMIBaaP4yQGftGjVHpBxn UjRjaMC/09Uhxgzsgiu4WWtMMbb9wRB2IVLLU0uaz1 Op8FT3Wri0Vxe1/aI6to0k6Kqvcbu3hvfL624bxXZdNV0/g10 rRl9nzC73AFWnkl51/A9LMt/XWOgFTPYixvK3OVvk/fvqT7oixns5dfL5WHvmr/UMyrUVRv0ZZJ1AQAAwJTNavjTrUNRoaC7TYWhqgO/lCRUWKroKjkdpquiOxpn9ZBTMnPbd1tAk6kq/R797p 9MmRnaWZAlsgWvoSsUKsqHqksaeg19rrAw5PcMb/r5 5Sl09txt8nzK79e2VQOuQ2v3WtRTq 1ykrX3xGBsfsrAC322an3OK39K2Szs0dcujx5yICndsltOObpZa lpvvk84rBuWZqLA4yboAAABg6mYx/OnWofB1Y570hsqRJ6Mk12dMa1VwlMzq4aZBxcPib9bpqdntc6a27 zMSk4y0lUjcLrdP1WAChwTb/vZ8i6hpkU1LZmI9TX2GvX/imsN3VbRmq2PtuunuWYz0Io5K 8TAAAAgBk1a HPDAKiQsaaqH5/wRAR4nYtNN1ETXhxBy RfhUkbLdRM0Jl8Ibpk2EHNfFvSfDsCsnqa L8IKrqqwek8W9rMIXt6 Dlrd8 eqRbeuvW2Xb/tFMuPQKpO3JmcH2m3lW7VDb2muT6bPhY2NE6S4O2RCkNkBMO9TP8PmF2Xb1GOiTYEjcqgw/1yaEbb5OOpXZWgDtaZ58859/a4YD07RiUlXfe4o/oWeKOBDr469KtHUaf/7n0vR1s3QuYZF0AAAAwdQvGx8cn7PMKqkxSqZSdAjDXDA8PSzqdloULJ/t3HH2t3XYVu6wrOuVhf1AWt0w2BwZ10df93aNCmZ0UfVu230298nG3eIbNnV6YdBfd3f9hfthKyUzkd2 GFO3wfw3teuq9hedF0A1HPq1ClxHEfa2trsHABAM8rn87JkyRI7NTWEP2Aem3r4A9AsCH8AEA8zEf44YwQAAACAGCD8AQAAAEAMEP4AAAAAIAYIfwAAAAAQA4Q/AAAAAIgBwh8AAAAAxADhDwAAAABigPAHzGP6/n76Hl8A4kv/BnCvTwBAI/jXApjH9I0 jx49KhMTE3YOgDjR3339GzDdm/4CAOKB8AfMY8lkUgqFgoyNjclnn31m5wKIA/2d1999/RugfwsAAKhnwfj4eNUmA1UmqVTKTgGYi06cOGFO/vT3lS6gQHzorp66xU8Hv8WLF9u5AIBmlc/np93Tg/AHAAAAAHPcTIQ/un0CAAAAQAwQ/gAAAAAgBgh/AAAAABADhD8AAAAAiAHCHwAAAADEAOEPAAAAAGKA8AcAAAAAMUD4AwAAAICmJ/L/AzX7mkLO4bowAAAAAElFTkSuQmCC[/IMG]
My router configuration has subnet mask as 255.255.0.0, does it matter or it is correct?

---

### Post by currentshaft on 2024-08-22
2

---

### Post by rahulsharma49 on 2024-08-23
made changes to YAML file but issue is still there, after some time i cant SSH or ping server.

It is connected to my router and i can access it from Cloudflare tunnel URL but cant access over local IP.

What can be wrong?

If there anything which i need to show you guys? please tell me

---

### Post by TheFu on 2024-08-23
10.0.0.100/8 does not map to 255.255.0.0.

I give up. We've told you already what is likely wrong and you've ignored it.  Probably should learn some basic IPv4 networking if you hope to get this solved.  I used to send people to read/listen to Ep 25 - 29 of _Security Now_ podcast ... "How the internet works", where IPv4 networking is laid out clearly.  There must be better guides these days. It isn't hard.

Most home users would have a /24 on their LAN which is the same as 255.255.255.0.  If you don't understand it, probably best to stay with what everyone else does until you do.

Additionally, many home routers prevent traffic that leaves and tries to return using the WAN IP.  Since I don't use Cloudflare tunnel, I don't know if that would be an issue or not.

---

### Post by rahulsharma49 on 2024-08-26
Bro changed both Router Subnet Mask to 255.255.255.0 and ip address on Ubuntu with /24 as suggested by all.

Still issue is there

---

### Post by TheFu on 2024-08-26
> **rahulsharma49 said:**
> Bro changed both Router Subnet Mask to 255.255.255.0 and ip address on Ubuntu with /24 as suggested by all.

Still issue is there

And still you haven't shown your work.  You haven't posted the suggested yaml file with the suggested updates. You didn't post the 2 netplan commands that must be run to generate and active the new YAML and there's no --debug or relevant lines from the system logs shown.  Very standard stuff for anyone choosing to run a "server".
With networking there are a few basic things.
[LIST]
[*]IP addresses
[*]network information
[*]routing tables
[/LIST]

If you remove the Cloudflare tunnel, does everything work as expected?  The basic steps for any troubleshooting is to 
[LIST=1]
[*]simplify 
[*]test, 
[*]repeat 
[/LIST]
until the thing that breaks it has been isolated and testing shows that 1 thing is the problem.  For something like this, perhaps 3 rounds of simply/test/repeat is my guess.

---

### Post by rahulsharma49 on 2024-08-28
Here is my updated YAML file
```
network:
  version: 2
  renderer: networkd
  wifis:
    wlp1s0:
      dhcp4: no
      dhcp6: no
      addresses: [10.0.0.100/24]
      nameservers:
        addresses: [10.0.0.1, 8.8.8.8]
      access-points:
        "mySSID":
          password: "mypassword"
      routes:
        - to: default
          via: 10.0.0.1



```

Two commands to generate and apply netplan are

[LIST]
[*]sudo netplan generate
[*]sudo netplan apply
[/LIST]

Removing cloudflare tunnel makes no difference

---

### Post by rahulsharma49 on 2024-09-02
is there any other logs which i can provide?

its very frustrating that server stops responding after sometime

---

