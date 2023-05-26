# Experimentálne otestovanie bezpečnostných modulov OS Linux

Cieľom tohto repozitára je otestovanie bezpečnostných modulov, SELinux a AppArmor, pomocou zraniteľností CVE. Nachádza 
sa tu niekoľko nakonfigurovaných priečikov, v ktoých sa nachádza súbor VAGRANT, ktorý slúži na automatické vytvorenie
virtuálnych prostredí. Pre bližšie opísanie konkrétnej zraniteľnosti, súbory obsahujú README. Pre otestovanie modulu
Apparmor používame distribúciu Ubuntu a pre otestovanie modulu Selinux používame distribúciu Fedora. Cieľom je bez
aktualizovania distribúcie otestovať zraniteľnosti. Jedinou inštaláciou sú potrebné aplikácie pre otestovanie zraniteľnosti. 

## Potrebné programy 

Pre spustenie VAGRANT súborov budeme potrebovať program Vagrant a VirtualBox.

Link na stiahnutie aplikácie Vagrant [https://developer.hashicorp.com/vagrant/downloads?product_intent=vagrant](https://developer.hashicorp.com/vagrant/downloads?product_intent=vagrant)

Link na stiahnutie aplikácie VirtualBox [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

## Vytvorenie virtuálnych prostredí

Následne si stiahnite priečinok pre vybraný útok a pomocou terminálu vytvoríme virtuálne prostedia.

V terminály prejdeme do priečinku pomocou príkazu `cd`:

```shell
C:\Users\user> cd "Downloads\CVE-2014-6271_Ubuntu"
```

Ostáva nám už len spustiť vagrant súbor pomocou príkazu `vagrant up`:

```shell
C:\Users\user\Downloads\CVE-2014-6271_Ubuntu> vagrant up
```

Teraz by sa mali sami nakonfigurovať a stiahnuť virtuálne prostredia. Automaticky sa otvorí distribúcia Kali Linux, ktorou 
budeme útočiť. Na pracovnej ploche sa nachádza súbor, ktorý automaticky zaútočí na potencionálne zraniteľný virtuálny stroj.

## Vypnutie a vymazanie virtuálnych prostredí

Pre vypnutie virtuálnych prostredí použijeme príkaz `vagrant halt`:

```shell
C:\Users\user\Downloads\CVE-2014-6271_Ubuntu> vagrant halt
```

Pre odstránenie virtuálnych prostredí použijeme príkaz `vagrant destroy`:

```shell
C:\Users\user\Downloads\CVE-2014-6271_Ubuntu> vagrant destroy
```

## Práca s Kali Linux

Meno aj heslo pre obe vituálne mašiny je `Vagrant`. Na pracovnej ploche sa nachádza súbor s názvom HACK. Po jeho rozkliknutí sa spustí automatický útok. Pokiaľ je útok 
úspešný v nástroji msfconsole vojdeme do interpretačného riadku meterpreter, v ktorom následne spustíme príkaz `shell`.
Po spustení príkazu sa dostaneme do konzoly shell na zraniteľnej mašine a môžme skúsiť následovné príkazy:

- `whoami` - povie nám aké máme privilégia

- `cat /etc/shadow` a `cat /etc/passwd` - vypíšemu nám obsah súborov shadow a passwd, pokiaľ máme oprávnenie


