# Block Trend Spammers

Bu proje Twitter trendlerini kullanarak trend kelime veya hashtag ile alakasız tweet atanlardan kurtulmaya çalışmayı amaçlamaktadır.
Twitter API limitleri nedeniyle tek seferde bu mümkün olmasada zaman zaman çalıştırarak en azından gereksiz pek çok kullanıcıyı engellemiş oluruz umarım!!!

## Açıklama
Kodu çalıştırmak için Twitter API erişimi olmalı ve API ayarlarınız "Read-Write" olmalıdır.
Öncelikle kendi Twitter API keylerinizi koda ekleyin.

```python
consumer_key = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
consumer_secret = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
access_token = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
access_token_secret = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
```

Daha sonra kodun analiz ayarları bölümünü kendinize göre doldurmalısınız.
```python
#Analiz için ayarlar
#TrendSpamPoint tweet içerisinde trend kelimelerden kaç tane geçtiğini gösterir.
minTrendSpamPoint = 3 #Belirlenenden daha az SpamPoint olanları seçme
maxFollowCount = 1000000 #Belirlenenden daha fazla takipçisi olanları seçme 
maxRetweetCount = 500 #Belirlenenden daha fazla retweet alanları seçme
maxUserCount = 5 #Her sorguda kaç tweet sorgulanacak. Twitter API limitlerini etkiler!!!
```

## Çalışma şekli

1. Twitter veya dataexport.io API'den güncel trend bilgilerini alır.
2. Alınan trend kelimeler dosyaya kaydedilir, dosya her seferinde güncellensin mi diye kullanıcıya sorulur.
3. Alınan trend kelimelerin her biri Twitterda aranır.
4. Bulunan tweetler "Analiz Ayarları" verilerine göre kontrol edilir. Şüpheli görülen kullanıcılar kaydedilir.
5. Kullanıcının kararına göre şüpheli kullanıcılar Engellenir, sessize alınır ya da hiçbir işlem yapılmaz.
6. son olarak engellenen, sessize alınan kullanıcılar ve analiz edilen tweetler dosyaya kaydedilir.
