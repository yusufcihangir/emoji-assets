# emoji-assets

Emoji Tahmin uygulaması için harici PNG görselleri. Uygulama bu depodan `raw.githubusercontent.com` üzerinden çeker; PNG yoksa Unicode emoji metnine düşer.

## Klasör yapısı

```
{mod}/
  {harf-sayısı}-harf/
    {seviye-id}/
      stage-1.png   ← 1. emoji aşaması
      stage-2.png   ← 2. aşama
      stage-3.png   ← 3. aşama (varsa)
```

### Mod klasörleri

| Klasör | Açıklama |
|--------|----------|
| `classic` | Ana seviye listesi |
| `countries` | Ülkeler modu |
| `footballers` | Futbolcular modu |
| `animals` | Hayvanlar modu |
| `professions` | Meslekler modu |

### Harf sayısı

Cevaptaki harf sayısı (boşluksuz): `FUTBOL` → `6-harf`, `AY` → `2-harf`.

### Örnek

Seviye 1, cevap `FUTBOL` (6 harf), klasik mod:

```
classic/6-harf/1/stage-1.png
classic/6-harf/1/stage-2.png
classic/6-harf/1/stage-3.png
```

## Görsel önerileri

- Format: PNG, şeffaf arka plan
- Boyut: en az 512×512 (kare); dikdörtgen kompozitler için 1024×512
- Dosya adı: küçük harf, `stage-1` … `stage-3`

## manifest.json (isteğe bağlı)

Depo kökünde `manifest.json` tutarsanız uygulama önce hangi seviyelerin PNG’si olduğunu okur (gereksiz istek azalır). Şema: `manifest.schema.json`.

## GitHub’a yükleme

Bu klasörü ayrı depo olarak yayınlayın:

```bash
cd emoji-assets
git init
git add .
git commit -m "Initial emoji-assets structure"
gh repo create yusufcihangir/emoji-assets --public --source=. --remote=origin --push
```

Uygulama varsayılan olarak `yusufcihangir/emoji-assets` deposunu kullanır. Farklı depo için `.env` içinde `EXPO_PUBLIC_EMOJI_ASSETS_REPO= kullanıcı/repo` ayarlayın.
