# 🌙 Pasaran Jawa — Kalender Weton & Google Kalender

Aplikasi web mobile untuk menghitung hari pasaran Jawa, weton, geblak/selamatan, dan integrasi langsung ke Google Kalender.

Terinspirasi dari [`lantip/pasaran`](https://github.com/lantip/pasaran).

## ✨ Fitur

| Tab | Keterangan |
|-----|-----------|
| **Hari Ini** | Tampilkan hari pasaran hari ini + logika *malem* (setelah Maghrib) + Wuku |
| **Kalender** | Tampilan kalender bulanan dengan label pasaran tiap tanggal, klik untuk add ke Google Kalender |
| **Cari Pasaran** | Cari semua tanggal dengan kombinasi hari + pasaran dalam setahun (mis: semua *Seloso Kliwon* 2025), bulk add ke Google Kalender |
| **Weton** | Cari weton untuk tanggal tertentu, add ke Google Kalender |
| **Geblak** | Hitung tanggal selamatan: Telung dina, Pitung dina, 40 dina, 100 dina, Pendhak I, Pendhak II, Nyewu (1000 hari) — add satu per satu atau sekaligus ke Google Kalender |

## 🧮 Algoritma

Berdasarkan kode asli dari [pasaran.py](https://github.com/lantip/pasaran/blob/master/pasaran.py):

```js
// Basis tanggal: 1 Januari 1800
const DATE_BASE = new Date(Date.UTC(1800, 0, 1));

function getPasIdx(date) {
  const d = new Date(Date.UTC(date.getFullYear(), date.getMonth(), date.getDate()));
  const diffDays = Math.floor((d - DATE_BASE) / 86400000);
  return ((diffDays % 5) + 5) % 5;
}
// Hasil: 0=Pon, 1=Wage, 2=Kliwon, 3=Legi, 4=Pahing
```

**Geblak** (dari `weton.py`):
| Nama | Hari ke- |
|------|----------|
| Geblak (hari meninggal) | 0 |
| Telung dina | 3 |
| Pitung dina | 7 |
| Patang puluh dina | 40 |
| Nyatus dina | 100 |
| Pendhak I | 354 (1 tahun Jawa) |
| Pendhak II | 708 (2 tahun Jawa) |
| Nyewu | 1000 |

## 🚀 Deploy

### Vercel (Recommended)

1. Fork/clone repo ini
2. Buka [vercel.com](https://vercel.com) → Import Project → pilih repo ini
3. Deploy (otomatis mendeteksi static site)

### Lokal

```bash
# Cukup buka langsung di browser
open index.html

# Atau pakai server lokal sederhana
npx serve .
python3 -m http.server 8080
```

## 📄 Lisensi

MIT — silakan digunakan dan dikembangkan bebas.

## 🙏 Credits

- Algoritma pasaran: [lantip/pasaran](https://github.com/lantip/pasaran)
- Nama Wuku 30: tradisi pawukon Jawa
