# Dijital Sistemler 2 🚀

## 📖 Genel Bakış
Bu GitHub deposu, Eskişehir Teknik Üniversitesi Elektrik ve Elektronik Mühendisliği Bölümü'nde EEM 334 - Dijital Sistemler II dersi kapsamında laboratuvarlarda gerçekleştirdiğim projeleri içermektedir. Depo, FPGA ve VHDL kullanarak dijital devre tasarımı, simülasyon ve uygulama konularında pratik örnekler sunar.

Bu depo, aşağıdaki amaçlar için faydalıdır:
- Dijital sistem tasarımı, VHDL programlama ve FPGA uygulamalarını öğrenmek.
- Kombinasyonel ve sıralı devreler, FSM gibi kavramları pratik projelerle anlamak.
- Xilinx ISE yazılımı ve Nexys4 FPGA kartı ile çalışma deneyimi kazanmak.

Depodaki projeler, laboratuvar föylerine dayalı olarak geliştirilmiş olup, her biri belirli bir dijital tasarım problemini çözer. Kodlar, VHDL dilinde yazılmış ve Xilinx ISE ortamında test edilmiştir. Projeler, temel FPGA tanıtımından başlayarak ALU tasarımı, dijital saat ve FSM gibi ileri seviye konulara uzanır.

## ✨ Temel Özellikler
- **LAB 1 - Xilinx ISE Yazılımı ve FPGA'ya Giriş**: ISE platformunun temel işlevlerini öğrenme, tasarım simülasyonu ve 4-bit toplayıcı devre tasarımı. 📚
- **LAB 2 - VHDL ve FPGA Donanım Uygulamasına Giriş**: VHDL kodları yazma, FPGA'ya yükleme ve 4-bit toplayıcıyı Nexys4 kartında uygulama. 🔧
- **LAB 3 - Kombinasyonel Devre Tasarımı**: Farklı eşzamanlı sinyal atama teknikleriyle kombinasyonel devre tasarımı, mantık fonksiyonları modülleri. ⚙️
- **LAB 4 - Kombinasyonel Mantık Devresi - ALU Tasarımı**: 4-bit ALU tasarımı (toplama, çıkarma, artırma, azaltma, AND, OR, XOR, NOT işlemleri). 🧮
- **LAB 5 - Sıralı Tasarım I - Dijital Saat**: Senkron sıralı devre tasarımı, yukarı-aşağı sayıcı ve dijital saat uygulaması. ⏰
- **LAB 6 - Sıralı Tasarım II - Dönen Kare**: Tek girişli paralel çıkışlı çift yönlü kaydırma kaydedicisi ile yedi segmentlerde dönen kareler. 🔄
- **LAB 7 - FSM Sıra Dedektörü**: FSM devresi tasarımı, seri veri girişi ile sıra algılama, son 8 girişi ve algılanan sıra sayısını gösterme. 🔍
- **Hata Yönetimi ve Simülasyon**: Her projede test bench'ler ile simülasyon ve FPGA yüklemesi için UCF dosyaları.

## 📋 Gereksinimler
Bu projeleri çalıştırmak için aşağıdaki gereksinimlere ihtiyacınız var. Uygulama, Windows için tasarlanmış olsa da Linux/macOS'a uyarlanabilir.

### Yazılım Bağımlılıkları:
- **Xilinx ISE 14.7+**: VHDL tasarımı ve simülasyon için. [xilinx.com](https://www.xilinx.com/support/download.html) adresinden indirin. 🛠️
- **VHDL Kütüphaneleri**: IEEE.std_logic_1164, numeric_std gibi standart kütüphaneler (ISE ile birlikte gelir).

### Donanım Gereksinimleri:
- **FPGA Kartı**: Nexys4 DDR veya benzeri Xilinx FPGA kartı (örneğin, Artix-7 tabanlı).
- **Bağlantı**: USB kablosu ile FPGA programlama.

**Platform Notları**: Projeler, Nexys4 DDR kartı için optimize edilmiştir. Diğer kartlar için UCF dosyalarını uyarlayın.

## 🛠️ Kurulum
Projeyi yerel makinenize kurmak için aşağıdaki adımları izleyin.

1. **Depoyu Klonlayın**:
   ```bash
   git clone https://github.com/yunuseemredogan/Digital-Systems-2.git
   cd Digital-Systems-2
   ```

2. **Xilinx ISE'yi Kurun**:
   - Xilinx ISE'yi indirin ve kurun.
   - Doğrulayın: ISE'yi açın ve yeni bir proje oluşturun.

3. **Opsiyonel: Ekran Görüntüleri Klasörü Oluşturun**:
   - README'ye resim eklemek isterseniz, `screenshots` klasörü oluşturun ve GUI yakalamalarını yükleyin.

## ▶️ Kullanım
Projeleri çalıştırmak oldukça basittir.

1. **Uygulamayı Başlatın**:
   - Xilinx ISE'yi açın.
   - Her lab için ilgili klasörü açın (örn. LAB1).

2. **Ayarları Yapılandır**:
   - VHDL dosyalarını derleyin.
   - Test bench ile simüle edin.
   - UCF dosyası ile pin atamalarını yapın.
   - FPGA'ya yükleyin (Synthesize, Implement, Generate Programming File, Program).

3. **İzleyin ve Durdurun**:
   - FPGA kartında sonuçları gözlemleyin (LED'ler, yedi segmentler).
   - Hata durumunda simülasyonu tekrarlayın.

4. **Alıcı Kurulumu (Bu Repo'da Yok)**:
   - Nexys4 kartı kullanın.

**Pro İpucu**: Önce simülasyonda test edin, sonra FPGA'ya yükleyin.

## 🔍 Nasıl Çalışır: İç Mekanizmalar
Projeler, VHDL ile dijital devreleri modelleme ve FPGA'ya uygulama üzerine kuruludur. İşte detaylı bir bakış.

### Üst Düzey İş Akışı (ASCII Diyagramı):
```
+-------------------+   VHDL   +-------------------+   ISE     +-------------------+
| Tasarım Aşaması   | --------> | Kodlama & Modül   | --------> | Simülasyon &      |
| (Föy & Diyagram)  |         | (Entity-Arch)     |           | Sentezleme        |
|                   |         |                   |           |                   |
+-------------------+         +-------------------+           +-------------------+
  |                                         |                          |
  v                                         v                          v
FPGA Yükleme                           Hata Günlüğü                Sonuç Gözlemleme
```

1. **Başlatma**:
   - Her lab, amaç ve arka plan ile başlar.
   - Modüller (entity-architecture) tanımlanır.

2. **Tasarım Adımı**:
   - Kombinasyonel: Eşzamanlı atamalar (when-else, with-select).
   - Sıralı: Process'ler ile flip-flop'lar, sayıcılar.

3. **Simülasyon**:
   - Test bench ile girişler uygulanır, çıkışlar doğrulanır.

4. **Uygulama**:
   - UCF ile pinler atanır, bit dosyası oluşturulur, FPGA'ya yüklenir.

Projeler, Nexys4 kartında 100MHz saat ile çalışır, ancak uyarlanabilir.

## 🧱 Kod Yapısı
Kodlar, modüler VHDL dosyalarından oluşur.

- **İmport'lar**: IEEE kütüphaneleri.
- **Entity**: Giriş/çıkış portları.
- **Architecture**: Davranışsal veya yapısal 구현.
- **Test Bench**: Simülasyon için.
- **UCF**: Pin atamaları.

Toplam satırlar: ~200-500/lab, yorumlarla net.

## ⚠️ Sorun Giderme
- **ISE Bulunamadı**: PATH'i kontrol edin.
- **Simülasyon Hataları**: Sintaksı kontrol edin.
- **Bağlantı Sorunları**: USB kablosu, sürücüler.
- **Yüksek CPU**: Basit tasarımlar.
- **Günlükler**: ISE konsolunu inceleyin.
- **Çökmeler**: ISE'de debug edin.

## 📉 Sınırlamalar
- Yalnızca Nexys4 için; diğer kartlara uyarlama gerekebilir.
- Temel simülasyon; gerçek zamanlı hata ayıklama yok.
- Şifreleme yok.
- Sabit ayarlar (saat cihazı); kodda özelleştirin.
- OS uyumsuzlukları.

## 🤝 Katkıda Bulunma
Depoyu fork edin, değişiklik yapın ve PR gönderin! Öneriler: Daha fazla lab ekleme, verimli kodlar, test senaryoları.

## 📜 Lisans
MIT Lisansı - Kullanın, değiştirin, paylaşın. [LICENSE](LICENSE) dosyasına bakın.

*2025'te ❤️ ile oluşturuldu. Soru veya geri bildirim için issue açın!*
