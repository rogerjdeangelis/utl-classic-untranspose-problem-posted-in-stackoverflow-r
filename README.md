# utl-classic-untranspose-problem-posted-in-stackoverflow-r
Classic untranspose problem posted in stackoverflow r
    Classic untranspose problem posted in stackoverflow r

    github
    https://tinyurl.com/y8vecc79
    https://github.com/rogerjdeangelis/utl-classic-untranspose-problem-posted-in-stackoverflow-r

        Two Solutions

              a. SAS untranspose macro
                 AUTHORS: Arthur Tabachneck, Gerhard Svolba, Joe Matise and Matt Kastin
                 https://www.analystfinder.com/about/

              b. R
                 AkRun
                 https://stackoverflow.com/users/3732271/akrun

    StackOverflow
    https://tinyurl.com/y9b2yj9a
    https://stackoverflow.com/questions/61445601/data-wrangling-from-wide-to-long-format-with-multiple-repeating-columns-of-diffe

    *_                   _
    (_)_ __  _ __  _   _| |_
    | | '_ \| '_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    ;

    data WORK.have;
      infile datalines dsd truncover;
      input ID:32. FRUIT_1:$7. DATE_1:MMDDYY10. NUMBER_1:32. FRUIT_2:$7.
    DATE_2:MMDDYY10. NUMBER_2:32. FRUIT_3:$7. DATE_3:MMDDYY10. NUMBER_3:32.;
    datalines4;
    1,raisin,04/07/2020,33,chili,02/22/2020,26,lime,03/23/2020,19
    2,lemon,02/29/2020,51,honeyde,02/28/2020,14,durian,04/14/2020,49
    3,cloudbe,03/17/2020,2,jujube,03/29/2020,94,cherimo,04/01/2020,16
    4,elderbe,03/03/2020,60,mandari,04/09/2020,74,raisin,01/05/2020,84
    5,nut,04/09/2020,53,lemon,03/17/2020,30,chili,03/14/2020,24
    ;;;;
    run;quit

    Up to 40 obs WORK.WANT total obs=5

    Obs    ID    FRUIT_1    DATE_1    NUMBER_1    FRUIT_2    DATE_2    NUMBER_2    FRUIT_3    DATE_3    NUMBER_3

     1      1    raisin      22012       33       chili       21967       26       lime        21997       19
     2      2    lemon       21974       51       honeyde     21973       14       durian      22019       49
     3      3    cloudbe     21991        2       jujube      22003       94       cherimo     22006       16
     4      4    elderbe     21977       60       mandari     22014       74       raisin      21919       84
     5      5    nut         22014       53       lemon       21991       30       chili       21988       24

    *            _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| '_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    ;

    WORK.WANT total obs=15

      ID   CLUSTER   DATE    FRUIT      NUMBER

       1      1     22012    raisin       33
       1      2     21967    chili        26
       1      3     21997    lime         19
       2      1     21974    lemon        51
       2      2     21973    honeyde      14
       2      3     22019    durian       49
       3      1     21991    cloudbe       2
       3      2     22003    jujube       94
       3      3     22006    cherimo      16
       4      1     21977    elderbe      60
       4      2     22014    mandari      74
       4      3     21919    raisin       84
       5      1     22014    nut          53
       5      2     21991    lemon        30
       5      3     21988    chili        24

    *
     _ __  _ __ ___   ___ ___  ___ ___
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    ;

    *                      _
      __ _     _   _ _ __ | |_ _ __ __ _ _ __  ___ _ __   ___  ___  ___
     / _` |   | | | | '_ \| __| '__/ _` | '_ \/ __| '_ \ / _ \/ __|/ _ \
    | (_| |_  | |_| | | | | |_| | | (_| | | | \__ \ |_) | (_) \__ \  __/
     \__,_(_)  \__,_|_| |_|\__|_|  \__,_|_| |_|___/ .__/ \___/|___/\___|
                                                  |_|
    ;

    %untranspose(data=have, out=want,by=id,id=cluster, delimiter=_, var=date fruit number)



         id cluster fruit        date       number
       <int> <chr>   <fct>        <date>      <int>
     1     1 1       olive        2020-04-21     50
     2     1 2       elderberry   2020-02-23     59
     3     1 3       cherimoya    2020-03-07      9
     4     2 1       jujube       2020-03-22     88
     5     2 2       mandarine    2020-03-06     45
     6     2 3       grape        2020-04-23     78
     7     3 1       nut          2020-01-26     53
     8     3 2       cantaloupe   2020-01-27     70
     9     3 3       durian       2020-02-15     39
    10     4 1       chili pepper 2020-03-17     60
    11     4 2       raisin       2020-04-14     20
    12     4 3       cloudberry   2020-03-11      4
    13     5 1       honeydew     2020-01-04     81
    14     5 2       lime         2020-03-23     53
    15     5 3       ugli fruit   2020-01-13     26

    *_
    | |__     _ __
    | '_ \   | '__|
    | |_) |  | |
    |_.__(_) |_|

    ;

    options validvarname=upcase;
    libname sd1 "d:/sd1";
    data sd1.have;
      infile datalines dsd truncover;
      input ID:32. FRUIT_1:$7. DATE_1:MMDDYY10. NUMBER_1:32. FRUIT_2:$7.
      DATE_2:MMDDYY10. NUMBER_2:32. FRUIT_3:$7. DATE_3:MMDDYY10. NUMBER_3:32.;
    datalines4;
    1,raisin,04/07/2020,33,chili,02/22/2020,26,lime,03/23/2020,19
    2,lemon,02/29/2020,51,honeyde,02/28/2020,14,durian,04/14/2020,49
    3,cloudbe,03/17/2020,2,jujube,03/29/2020,94,cherimo,04/01/2020,16
    4,elderbe,03/03/2020,60,mandari,04/09/2020,74,raisin,01/05/2020,84
    5,nut,04/09/2020,53,lemon,03/17/2020,30,chili,03/14/2020,24
    ;;;;
    run;quit

    %utl_submit_r64('
    library(tidyr);
    library(dplyr);
    library(haven);
    library(SASxport);
    library(data.table);
    have<-read_sas("d:/sd1/have.sas7bdat");
    want<-melt(setDT(have), measure = patterns("^FRUIT", "^DATE", "^NUMBER" ),
          value.name = c("FRUIT", "DATE", "NUMBER"), variable.name = "CLUSTER");
    write.xport(want,file="d:/xpt/want.xpt");
    ');

    libname xpt xport "d:/xpt/want.xpt";
    data want;
      set xpt.want;
    run;quit;
    libname xpt clear;


