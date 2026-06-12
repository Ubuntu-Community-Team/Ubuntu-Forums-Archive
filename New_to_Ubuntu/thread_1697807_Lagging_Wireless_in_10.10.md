---
title: "Lagging Wireless in 10.10"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by SanjoEel on 2011-03-01
Hey folks, 
I tried really hard to diagnose this but I am a little perplexed with this one. Every so often (like every 5-10 minutes) my wireless connections slows tremendously. Signal strength is excellent, and it only does it on my 10.10 machine. Windows and other Ubuntu machines on the same network do not lag. I would be grateful for suggestions on where to start troubleshooting this.
Machine is a Toshiba Satellite a665-6058 laptop running Ubuntu 10.10.
Tell me what info you need and I'll post it.
Thanks in advance...
Sanjo
:)

---

### Post by SanjoEel on 2011-03-01
dmesg output, if this helps
> [ 1054.910724] =====>rtl8192_set_chan()====ch:6
[ 1055.030667] =====>rtl8192_set_chan()====ch:7
[ 1055.150032] =====>rtl8192_set_chan()====ch:8
[ 1055.263369] =====>rtl8192_set_chan()====ch:9
[ 1055.380688] =====>rtl8192_set_chan()====ch:10
[ 1055.500433] =====>rtl8192_set_chan()====ch:11
[ 1055.610672] =====>rtl8192_set_chan()====ch:12
[ 1055.730690] =====>rtl8192_set_chan()====ch:13
[ 1055.850066] =====>rtl8192_set_chan()====ch:11
[ 1055.860247] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1055.860254] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 1174.232106] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1174.290824] =====>rtl8192_set_chan()====ch:1
[ 1174.410671] =====>rtl8192_set_chan()====ch:2
[ 1174.530072] =====>rtl8192_set_chan()====ch:3
[ 1174.640067] =====>rtl8192_set_chan()====ch:4
[ 1174.750083] =====>rtl8192_set_chan()====ch:5
[ 1174.860074] =====>rtl8192_set_chan()====ch:6
[ 1174.980672] =====>rtl8192_set_chan()====ch:7
[ 1175.100690] =====>rtl8192_set_chan()====ch:8
[ 1175.222117] =====>rtl8192_set_chan()====ch:9
[ 1175.340082] =====>rtl8192_set_chan()====ch:10
[ 1175.460692] =====>rtl8192_set_chan()====ch:11
[ 1175.580067] =====>rtl8192_set_chan()====ch:12
[ 1175.700948] =====>rtl8192_set_chan()====ch:13
[ 1175.820668] =====>rtl8192_set_chan()====ch:11
[ 1175.830942] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1175.830950] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 1223.279923] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1231.311203] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1294.233351] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1294.233483] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1294.300124] =====>rtl8192_set_chan()====ch:1
[ 1294.420203] =====>rtl8192_set_chan()====ch:2
[ 1294.540074] =====>rtl8192_set_chan()====ch:3
[ 1294.660083] =====>rtl8192_set_chan()====ch:4
[ 1294.780082] =====>rtl8192_set_chan()====ch:5
[ 1294.900051] =====>rtl8192_set_chan()====ch:6
[ 1295.020040] =====>rtl8192_set_chan()====ch:7
[ 1295.147913] =====>rtl8192_set_chan()====ch:8
[ 1295.260041] =====>rtl8192_set_chan()====ch:9
[ 1295.370040] =====>rtl8192_set_chan()====ch:10
[ 1295.480043] =====>rtl8192_set_chan()====ch:11
[ 1295.590039] =====>rtl8192_set_chan()====ch:12
[ 1295.710037] =====>rtl8192_set_chan()====ch:13
[ 1295.820054] =====>rtl8192_set_chan()====ch:11
[ 1295.830262] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1295.830270] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 1414.231451] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1414.231564] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1414.299497] =====>rtl8192_set_chan()====ch:1
[ 1414.410077] =====>rtl8192_set_chan()====ch:2
[ 1414.531245] =====>rtl8192_set_chan()====ch:3
[ 1414.650068] =====>rtl8192_set_chan()====ch:4
[ 1414.770068] =====>rtl8192_set_chan()====ch:5
[ 1414.890066] =====>rtl8192_set_chan()====ch:6
[ 1415.010083] =====>rtl8192_set_chan()====ch:7
[ 1415.130081] =====>rtl8192_set_chan()====ch:8
[ 1415.252971] =====>rtl8192_set_chan()====ch:9
[ 1415.375352] =====>rtl8192_set_chan()====ch:10
[ 1415.490030] =====>rtl8192_set_chan()====ch:11
[ 1415.610067] =====>rtl8192_set_chan()====ch:12
[ 1415.730064] =====>rtl8192_set_chan()====ch:13
[ 1415.850079] =====>rtl8192_set_chan()====ch:11
[ 1415.860280] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1415.860287] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 1534.231418] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1534.231533] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1534.300132] =====>rtl8192_set_chan()====ch:1
[ 1534.421976] =====>rtl8192_set_chan()====ch:2
[ 1534.540066] =====>rtl8192_set_chan()====ch:3
[ 1534.660086] =====>rtl8192_set_chan()====ch:4
[ 1534.780036] =====>rtl8192_set_chan()====ch:5
[ 1534.900056] =====>rtl8192_set_chan()====ch:6
[ 1535.020071] =====>rtl8192_set_chan()====ch:7
[ 1535.140087] =====>rtl8192_set_chan()====ch:8
[ 1535.260066] =====>rtl8192_set_chan()====ch:9
[ 1535.380066] =====>rtl8192_set_chan()====ch:10
[ 1535.492542] =====>rtl8192_set_chan()====ch:11
[ 1535.610068] =====>rtl8192_set_chan()====ch:12
[ 1535.730099] =====>rtl8192_set_chan()====ch:13
[ 1535.850085] =====>rtl8192_set_chan()====ch:11
[ 1535.860293] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1535.860300] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 1654.233139] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1654.233252] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1654.299132] =====>rtl8192_set_chan()====ch:1
[ 1654.420660] =====>rtl8192_set_chan()====ch:2
[ 1654.540722] =====>rtl8192_set_chan()====ch:3
[ 1654.662505] =====>rtl8192_set_chan()====ch:4
[ 1654.790720] =====>rtl8192_set_chan()====ch:5
[ 1654.916838] =====>rtl8192_set_chan()====ch:6
[ 1655.035815] =====>rtl8192_set_chan()====ch:7
[ 1655.153904] =====>rtl8192_set_chan()====ch:8
[ 1655.272320] =====>rtl8192_set_chan()====ch:9
[ 1655.390108] =====>rtl8192_set_chan()====ch:10
[ 1655.510689] =====>rtl8192_set_chan()====ch:11
[ 1655.630716] =====>rtl8192_set_chan()====ch:12
[ 1655.752949] =====>rtl8192_set_chan()====ch:13
[ 1655.880729] =====>rtl8192_set_chan()====ch:11
[ 1655.890931] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1655.890938] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 1676.200060] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1701.290317] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1713.370253] too short to sleep::2281e, 22819, 5
[ 1834.281005] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1834.281118] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1834.340105] =====>rtl8192_set_chan()====ch:1
[ 1834.460061] =====>rtl8192_set_chan()====ch:2
[ 1834.580078] =====>rtl8192_set_chan()====ch:3
[ 1834.700065] =====>rtl8192_set_chan()====ch:4
[ 1834.830084] =====>rtl8192_set_chan()====ch:5
[ 1834.950060] =====>rtl8192_set_chan()====ch:6
[ 1835.070086] =====>rtl8192_set_chan()====ch:7
[ 1835.190065] =====>rtl8192_set_chan()====ch:8
[ 1835.310068] =====>rtl8192_set_chan()====ch:9
[ 1835.430087] =====>rtl8192_set_chan()====ch:10
[ 1835.550071] =====>rtl8192_set_chan()====ch:11
[ 1835.670056] =====>rtl8192_set_chan()====ch:12
[ 1835.790086] =====>rtl8192_set_chan()====ch:13
[ 1835.910071] =====>rtl8192_set_chan()====ch:11
[ 1835.920277] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1835.920287] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 1861.340445] too short to sleep::261eb, 261e6, 5
[ 1894.233152] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 1894.233277] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1894.290720] =====>rtl8192_set_chan()====ch:1
[ 1894.410672] =====>rtl8192_set_chan()====ch:2
[ 1894.530089] =====>rtl8192_set_chan()====ch:3
[ 1894.640682] =====>rtl8192_set_chan()====ch:4
[ 1894.760087] =====>rtl8192_set_chan()====ch:5
[ 1894.870722] =====>rtl8192_set_chan()====ch:6
[ 1894.990708] =====>rtl8192_set_chan()====ch:7
[ 1895.110089] =====>rtl8192_set_chan()====ch:8
[ 1895.230677] =====>rtl8192_set_chan()====ch:9
[ 1895.350087] =====>rtl8192_set_chan()====ch:10
[ 1895.460676] =====>rtl8192_set_chan()====ch:11
[ 1895.580112] =====>rtl8192_set_chan()====ch:12
[ 1895.690707] =====>rtl8192_set_chan()====ch:13
[ 1895.820661] =====>rtl8192_set_chan()====ch:11
[ 1895.830863] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 1895.830872] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 2014.232671] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2014.300098] =====>rtl8192_set_chan()====ch:1
[ 2014.430038] =====>rtl8192_set_chan()====ch:2
[ 2014.560045] =====>rtl8192_set_chan()====ch:3
[ 2014.670050] =====>rtl8192_set_chan()====ch:4
[ 2014.780048] =====>rtl8192_set_chan()====ch:5
[ 2014.890032] =====>rtl8192_set_chan()====ch:6
[ 2015.017887] =====>rtl8192_set_chan()====ch:7
[ 2015.140067] =====>rtl8192_set_chan()====ch:8
[ 2015.260041] =====>rtl8192_set_chan()====ch:9
[ 2015.380053] =====>rtl8192_set_chan()====ch:10
[ 2015.500055] =====>rtl8192_set_chan()====ch:11
[ 2015.620055] =====>rtl8192_set_chan()====ch:12
[ 2015.740055] =====>rtl8192_set_chan()====ch:13
[ 2015.860037] =====>rtl8192_set_chan()====ch:11
[ 2015.870238] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2015.870245] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 2043.410282] too short to sleep::2a90a, 2a905, 5
[ 2134.231281] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2134.290878] =====>rtl8192_set_chan()====ch:1
[ 2134.410722] =====>rtl8192_set_chan()====ch:2
[ 2134.530033] =====>rtl8192_set_chan()====ch:3
[ 2134.640057] =====>rtl8192_set_chan()====ch:4
[ 2134.750087] =====>rtl8192_set_chan()====ch:5
[ 2134.860708] =====>rtl8192_set_chan()====ch:6
[ 2134.986151] =====>rtl8192_set_chan()====ch:7
[ 2135.100070] =====>rtl8192_set_chan()====ch:8
[ 2135.210831] =====>rtl8192_set_chan()====ch:9
[ 2135.330657] =====>rtl8192_set_chan()====ch:10
[ 2135.450673] =====>rtl8192_set_chan()====ch:11
[ 2135.570102] =====>rtl8192_set_chan()====ch:12
[ 2135.680085] =====>rtl8192_set_chan()====ch:13
[ 2135.790699] =====>rtl8192_set_chan()====ch:11
[ 2135.800963] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2135.800970] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 2179.607785] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2254.232210] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2254.290382] =====>rtl8192_set_chan()====ch:1
[ 2254.406881] =====>rtl8192_set_chan()====ch:2
[ 2254.520090] =====>rtl8192_set_chan()====ch:3
[ 2254.640047] =====>rtl8192_set_chan()====ch:4
[ 2254.760054] =====>rtl8192_set_chan()====ch:5
[ 2254.880079] =====>rtl8192_set_chan()====ch:6
[ 2255.000090] =====>rtl8192_set_chan()====ch:7
[ 2255.120066] =====>rtl8192_set_chan()====ch:8
[ 2255.240069] =====>rtl8192_set_chan()====ch:9
[ 2255.360056] =====>rtl8192_set_chan()====ch:10
[ 2255.490058] =====>rtl8192_set_chan()====ch:11
[ 2255.620059] =====>rtl8192_set_chan()====ch:12
[ 2255.740048] =====>rtl8192_set_chan()====ch:13
[ 2255.850069] =====>rtl8192_set_chan()====ch:11
[ 2255.860268] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2255.860278] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 2354.406610] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2358.090101] too short to sleep::323f6, 323f1, 5
[ 2359.313086] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2374.231243] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2374.290739] =====>rtl8192_set_chan()====ch:1
[ 2374.410659] =====>rtl8192_set_chan()====ch:2
[ 2374.540680] =====>rtl8192_set_chan()====ch:3
[ 2374.670710] =====>rtl8192_set_chan()====ch:4
[ 2374.790685] =====>rtl8192_set_chan()====ch:5
[ 2374.910376] =====>rtl8192_set_chan()====ch:6
[ 2375.020656] =====>rtl8192_set_chan()====ch:7
[ 2375.140428] =====>rtl8192_set_chan()====ch:8
[ 2375.260659] =====>rtl8192_set_chan()====ch:9
[ 2375.380689] =====>rtl8192_set_chan()====ch:10
[ 2375.500420] =====>rtl8192_set_chan()====ch:11
[ 2375.610649] =====>rtl8192_set_chan()====ch:12
[ 2375.730679] =====>rtl8192_set_chan()====ch:13
[ 2375.853516] =====>rtl8192_set_chan()====ch:11
[ 2375.863760] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2375.863768] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 2398.640745] too short to sleep::333cd, 333c8, 5
[ 2439.400244] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2494.231481] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2494.231605] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2494.290149] =====>rtl8192_set_chan()====ch:1
[ 2494.410083] =====>rtl8192_set_chan()====ch:2
[ 2494.530087] =====>rtl8192_set_chan()====ch:3
[ 2494.650056] =====>rtl8192_set_chan()====ch:4
[ 2494.770089] =====>rtl8192_set_chan()====ch:5
[ 2494.890084] =====>rtl8192_set_chan()====ch:6
[ 2495.010050] =====>rtl8192_set_chan()====ch:7
[ 2495.130083] =====>rtl8192_set_chan()====ch:8
[ 2495.250057] =====>rtl8192_set_chan()====ch:9
[ 2495.370070] =====>rtl8192_set_chan()====ch:10
[ 2495.490091] =====>rtl8192_set_chan()====ch:11
[ 2495.610057] =====>rtl8192_set_chan()====ch:12
[ 2495.730074] =====>rtl8192_set_chan()====ch:13
[ 2495.852686] =====>rtl8192_set_chan()====ch:11
[ 2495.862878] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2495.862884] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 2614.232056] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2614.232178] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2614.290476] =====>rtl8192_set_chan()====ch:1
[ 2614.410649] =====>rtl8192_set_chan()====ch:2
[ 2614.530657] =====>rtl8192_set_chan()====ch:3
[ 2614.650057] =====>rtl8192_set_chan()====ch:4
[ 2614.760723] =====>rtl8192_set_chan()====ch:5
[ 2614.880052] =====>rtl8192_set_chan()====ch:6
[ 2614.990656] =====>rtl8192_set_chan()====ch:7
[ 2615.110660] =====>rtl8192_set_chan()====ch:8
[ 2615.230690] =====>rtl8192_set_chan()====ch:9
[ 2615.350071] =====>rtl8192_set_chan()====ch:10
[ 2615.460097] =====>rtl8192_set_chan()====ch:11
[ 2615.570058] =====>rtl8192_set_chan()====ch:12
[ 2615.680064] =====>rtl8192_set_chan()====ch:13
[ 2615.790091] =====>rtl8192_set_chan()====ch:11
[ 2615.800272] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2615.800278] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 2694.992386] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2734.231495] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2734.231607] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2734.290720] =====>rtl8192_set_chan()====ch:1
[ 2734.410088] =====>rtl8192_set_chan()====ch:2
[ 2734.530726] =====>rtl8192_set_chan()====ch:3
[ 2734.650058] =====>rtl8192_set_chan()====ch:4
[ 2734.760052] =====>rtl8192_set_chan()====ch:5
[ 2734.870053] =====>rtl8192_set_chan()====ch:6
[ 2734.980684] =====>rtl8192_set_chan()====ch:7
[ 2735.100683] =====>rtl8192_set_chan()====ch:8
[ 2735.220670] =====>rtl8192_set_chan()====ch:9
[ 2735.340054] =====>rtl8192_set_chan()====ch:10
[ 2735.450683] =====>rtl8192_set_chan()====ch:11
[ 2735.570669] =====>rtl8192_set_chan()====ch:12
[ 2735.690682] =====>rtl8192_set_chan()====ch:13
[ 2735.810715] =====>rtl8192_set_chan()====ch:11
[ 2735.820913] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2735.820920] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 2854.232111] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2854.232203] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2854.290734] =====>rtl8192_set_chan()====ch:1
[ 2854.419557] =====>rtl8192_set_chan()====ch:2
[ 2854.533672] =====>rtl8192_set_chan()====ch:3
[ 2854.653844] =====>rtl8192_set_chan()====ch:4
[ 2854.772479] =====>rtl8192_set_chan()====ch:5
[ 2854.899897] =====>rtl8192_set_chan()====ch:6
[ 2855.016248] =====>rtl8192_set_chan()====ch:7
[ 2855.133762] =====>rtl8192_set_chan()====ch:8
[ 2855.250680] =====>rtl8192_set_chan()====ch:9
[ 2855.373391] =====>rtl8192_set_chan()====ch:10
[ 2855.490672] =====>rtl8192_set_chan()====ch:11
[ 2855.610674] =====>rtl8192_set_chan()====ch:12
[ 2855.730640] =====>rtl8192_set_chan()====ch:13
[ 2855.852945] =====>rtl8192_set_chan()====ch:11
[ 2855.863142] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2855.863149] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 2974.231118] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 2974.231221] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2974.282365] =====>rtl8192_set_chan()====ch:1
[ 2974.402841] =====>rtl8192_set_chan()====ch:2
[ 2974.530054] =====>rtl8192_set_chan()====ch:3
[ 2974.650073] =====>rtl8192_set_chan()====ch:4
[ 2974.770054] =====>rtl8192_set_chan()====ch:5
[ 2974.890050] =====>rtl8192_set_chan()====ch:6
[ 2975.010080] =====>rtl8192_set_chan()====ch:7
[ 2975.130030] =====>rtl8192_set_chan()====ch:8
[ 2975.250026] =====>rtl8192_set_chan()====ch:9
[ 2975.370090] =====>rtl8192_set_chan()====ch:10
[ 2975.494099] =====>rtl8192_set_chan()====ch:11
[ 2975.610030] =====>rtl8192_set_chan()====ch:12
[ 2975.730057] =====>rtl8192_set_chan()====ch:13
[ 2975.850045] =====>rtl8192_set_chan()====ch:11
[ 2975.860292] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2975.860299] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 3094.231618] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3094.231721] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3094.300776] =====>rtl8192_set_chan()====ch:1
[ 3094.420659] =====>rtl8192_set_chan()====ch:2
[ 3094.540075] =====>rtl8192_set_chan()====ch:3
[ 3094.650090] =====>rtl8192_set_chan()====ch:4
[ 3094.770074] =====>rtl8192_set_chan()====ch:5
[ 3094.890081] =====>rtl8192_set_chan()====ch:6
[ 3095.000072] =====>rtl8192_set_chan()====ch:7
[ 3095.110101] =====>rtl8192_set_chan()====ch:8
[ 3095.220068] =====>rtl8192_set_chan()====ch:9
[ 3095.330037] =====>rtl8192_set_chan()====ch:10
[ 3095.450692] =====>rtl8192_set_chan()====ch:11
[ 3095.570055] =====>rtl8192_set_chan()====ch:12
[ 3095.680722] =====>rtl8192_set_chan()====ch:13
[ 3095.800717] =====>rtl8192_set_chan()====ch:11
[ 3095.810920] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3095.810926] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 3214.233259] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3214.233361] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3214.295298] =====>rtl8192_set_chan()====ch:1
[ 3214.410702] =====>rtl8192_set_chan()====ch:2
[ 3214.530057] =====>rtl8192_set_chan()====ch:3
[ 3214.640683] =====>rtl8192_set_chan()====ch:4
[ 3214.760650] =====>rtl8192_set_chan()====ch:5
[ 3214.880674] =====>rtl8192_set_chan()====ch:6
[ 3215.000684] =====>rtl8192_set_chan()====ch:7
[ 3215.120683] =====>rtl8192_set_chan()====ch:8
[ 3215.245776] =====>rtl8192_set_chan()====ch:9
[ 3215.360648] =====>rtl8192_set_chan()====ch:10
[ 3215.480074] =====>rtl8192_set_chan()====ch:11
[ 3215.590063] =====>rtl8192_set_chan()====ch:12
[ 3215.700662] =====>rtl8192_set_chan()====ch:13
[ 3215.820691] =====>rtl8192_set_chan()====ch:11
[ 3215.830896] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3215.830906] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 3238.232557] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3266.701973] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3307.150617] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3334.231816] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3334.300877] =====>rtl8192_set_chan()====ch:1
[ 3334.420703] =====>rtl8192_set_chan()====ch:2
[ 3334.530105] =====>rtl8192_set_chan()====ch:3
[ 3334.640086] =====>rtl8192_set_chan()====ch:4
[ 3334.750707] =====>rtl8192_set_chan()====ch:5
[ 3334.870059] =====>rtl8192_set_chan()====ch:6
[ 3334.980674] =====>rtl8192_set_chan()====ch:7
[ 3335.100718] =====>rtl8192_set_chan()====ch:8
[ 3335.220068] =====>rtl8192_set_chan()====ch:9
[ 3335.330110] =====>rtl8192_set_chan()====ch:10
[ 3335.440039] =====>rtl8192_set_chan()====ch:11
[ 3335.560033] =====>rtl8192_set_chan()====ch:12
[ 3335.670085] =====>rtl8192_set_chan()====ch:13
[ 3335.780099] =====>rtl8192_set_chan()====ch:11
[ 3335.790348] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3335.790355] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 3399.410789] too short to sleep::4baba, 4bab5, 5
[ 3454.232060] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3454.290881] =====>rtl8192_set_chan()====ch:1
[ 3454.420569] =====>rtl8192_set_chan()====ch:2
[ 3454.542472] =====>rtl8192_set_chan()====ch:3
[ 3454.660056] =====>rtl8192_set_chan()====ch:4
[ 3454.780030] =====>rtl8192_set_chan()====ch:5
[ 3454.900029] =====>rtl8192_set_chan()====ch:6
[ 3455.021617] =====>rtl8192_set_chan()====ch:7
[ 3455.140043] =====>rtl8192_set_chan()====ch:8
[ 3455.260048] =====>rtl8192_set_chan()====ch:9
[ 3455.380049] =====>rtl8192_set_chan()====ch:10
[ 3455.500045] =====>rtl8192_set_chan()====ch:11
[ 3455.623840] =====>rtl8192_set_chan()====ch:12
[ 3455.740045] =====>rtl8192_set_chan()====ch:13
[ 3455.860057] =====>rtl8192_set_chan()====ch:11
[ 3455.870263] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3455.870267] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 3515.945127] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3574.231466] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3574.290140] =====>rtl8192_set_chan()====ch:1
[ 3574.420035] =====>rtl8192_set_chan()====ch:2
[ 3574.540059] =====>rtl8192_set_chan()====ch:3
[ 3574.660056] =====>rtl8192_set_chan()====ch:4
[ 3574.780027] =====>rtl8192_set_chan()====ch:5
[ 3574.900056] =====>rtl8192_set_chan()====ch:6
[ 3575.020057] =====>rtl8192_set_chan()====ch:7
[ 3575.140068] =====>rtl8192_set_chan()====ch:8
[ 3575.260055] =====>rtl8192_set_chan()====ch:9
[ 3575.381209] =====>rtl8192_set_chan()====ch:10
[ 3575.500052] =====>rtl8192_set_chan()====ch:11
[ 3575.620033] =====>rtl8192_set_chan()====ch:12
[ 3575.740055] =====>rtl8192_set_chan()====ch:13
[ 3575.860064] =====>rtl8192_set_chan()====ch:11
[ 3575.870261] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3575.870267] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 3605.340276] too short to sleep::50b2b, 50b26, 5
[ 3643.311057] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3655.310730] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3694.233622] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3694.233758] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3694.297205] =====>rtl8192_set_chan()====ch:1
[ 3694.410047] =====>rtl8192_set_chan()====ch:2
[ 3694.540068] =====>rtl8192_set_chan()====ch:3
[ 3694.664693] =====>rtl8192_set_chan()====ch:4
[ 3694.780092] =====>rtl8192_set_chan()====ch:5
[ 3694.900044] =====>rtl8192_set_chan()====ch:6
[ 3695.020072] =====>rtl8192_set_chan()====ch:7
[ 3695.140053] =====>rtl8192_set_chan()====ch:8
[ 3695.260480] =====>rtl8192_set_chan()====ch:9
[ 3695.380053] =====>rtl8192_set_chan()====ch:10
[ 3695.500087] =====>rtl8192_set_chan()====ch:11
[ 3695.620071] =====>rtl8192_set_chan()====ch:12
[ 3695.740055] =====>rtl8192_set_chan()====ch:13
[ 3695.860082] =====>rtl8192_set_chan()====ch:11
[ 3695.870286] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3695.870293] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 3755.310743] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3806.152979] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3814.230316] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3814.290220] =====>rtl8192_set_chan()====ch:1
[ 3814.410063] =====>rtl8192_set_chan()====ch:2
[ 3814.530717] =====>rtl8192_set_chan()====ch:3
[ 3814.650687] =====>rtl8192_set_chan()====ch:4
[ 3814.770708] =====>rtl8192_set_chan()====ch:5
[ 3814.890087] =====>rtl8192_set_chan()====ch:6
[ 3815.000078] =====>rtl8192_set_chan()====ch:7
[ 3815.110057] =====>rtl8192_set_chan()====ch:8
[ 3815.220060] =====>rtl8192_set_chan()====ch:9
[ 3815.330685] =====>rtl8192_set_chan()====ch:10
[ 3815.450064] =====>rtl8192_set_chan()====ch:11
[ 3815.567046] =====>rtl8192_set_chan()====ch:12
[ 3815.680707] =====>rtl8192_set_chan()====ch:13
[ 3815.800726] =====>rtl8192_set_chan()====ch:11
[ 3815.810989] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3815.810995] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 3826.633056] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3885.514137] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3934.232230] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3934.290818] =====>rtl8192_set_chan()====ch:1
[ 3934.410031] =====>rtl8192_set_chan()====ch:2
[ 3934.530649] =====>rtl8192_set_chan()====ch:3
[ 3934.650657] =====>rtl8192_set_chan()====ch:4
[ 3934.770656] =====>rtl8192_set_chan()====ch:5
[ 3934.890193] =====>rtl8192_set_chan()====ch:6
[ 3935.000033] =====>rtl8192_set_chan()====ch:7
[ 3935.120648] =====>rtl8192_set_chan()====ch:8
[ 3935.240644] =====>rtl8192_set_chan()====ch:9
[ 3935.360647] =====>rtl8192_set_chan()====ch:10
[ 3935.482761] =====>rtl8192_set_chan()====ch:11
[ 3935.600654] =====>rtl8192_set_chan()====ch:12
[ 3935.720034] =====>rtl8192_set_chan()====ch:13
[ 3935.840245] =====>rtl8192_set_chan()====ch:11
[ 3935.850500] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 3935.850508] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 4064.236898] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4064.290842] =====>rtl8192_set_chan()====ch:1
[ 4064.410650] =====>rtl8192_set_chan()====ch:2
[ 4064.534628] =====>rtl8192_set_chan()====ch:3
[ 4064.650667] =====>rtl8192_set_chan()====ch:4
[ 4064.770694] =====>rtl8192_set_chan()====ch:5
[ 4064.890680] =====>rtl8192_set_chan()====ch:6
[ 4065.020693] =====>rtl8192_set_chan()====ch:7
[ 4065.140692] =====>rtl8192_set_chan()====ch:8
[ 4065.252403] =====>rtl8192_set_chan()====ch:9
[ 4065.370695] =====>rtl8192_set_chan()====ch:10
[ 4065.491600] =====>rtl8192_set_chan()====ch:11
[ 4065.610721] =====>rtl8192_set_chan()====ch:12
[ 4065.736172] =====>rtl8192_set_chan()====ch:13
[ 4065.854667] =====>rtl8192_set_chan()====ch:11
[ 4065.864935] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 4065.864944] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 4109.360201] too short to sleep::5d00d, 5d008, 5


---

### Post by SanjoEel on 2011-03-01
Disabling IPv6 seems to have solved the problem.

---

### Post by SanjoEel on 2011-03-01
Well, disabling IPv6 helped, but the issue persists.
Whenever the network slows way down I run dmesg and get this or similar every time:

[ 2996.810293] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 2996.810302] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[ 3008.141447] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 3014.797471] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData

What's going on here, can someone please advise?

---

