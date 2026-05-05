# Analytics dashboard — landing page de servicios (salud y bienestar)
## Firebase Hosting · Google Analytics 4 · Looker Studio

![Firebase](https://img.shields.io/badge/Firebase-Hosting-orange)
![Google Analytics](https://img.shields.io/badge/Google%20Analytics-4-blue)
![Looker Studio](https://img.shields.io/badge/Looker-Studio-4285F4)
![Status](https://img.shields.io/badge/Status-Live-brightgreen)

---

## Descripción

Implementación de analítica web para un cliente del rubro salud y bienestar con sitio estático en Firebase Hosting. El objetivo era entender si la estrategia de contenido generaba tráfico real y si los usuarios navegaban el sitio o se iban desde la home. La solución conecta GA4 al sitio existente sin modificar la lógica de negocio, y expone los datos en un dashboard de Looker Studio accesible para el cliente sin necesidad de entrar a Firebase ni tener conocimientos técnicos.

---

## Contexto y problema

El cliente tenía un sitio funcional pero sin ninguna métrica de uso. No sabía si la estrategia de contenido traía visitas, si los usuarios exploraban más allá de la home, ni qué páginas no aportaban valor.

Las preguntas concretas que guiaron el proyecto:

- ¿Hay tráfico real o el sitio está inactivo?
- ¿Los usuarios se quedan o rebotan desde la home?
- ¿Qué páginas tienen más visitas y cuáles se pueden eliminar o fusionar?
- ¿El tráfico es nuevo (estrategia de adquisición) o recurrente (fidelización)?

---

## Stack

| Capa | Tecnología | Rol |
|------|------------|-----|
| Hosting | Firebase Hosting | Sirve el sitio estático |
| Medición | Google Analytics 4 | Captura eventos y sesiones |
| Visualización | Google Looker Studio | Dashboard para el cliente |
| Código | HTML / CSS / JavaScript (Vanilla) | Frontend del sitio |

> El plan gratuito de Firebase (Spark) es suficiente para toda la implementación.  
> BigQuery no es necesario: GA4 se conecta directo a Looker Studio sin costo adicional.

---

## Métricas relevadas

### Tráfico — ¿hay movimiento?
- **Usuarios** y **sesiones** → indica si la estrategia genera visitas reales
- **Usuarios nuevos vs recurrentes** → evalúa adquisición vs fidelización

### Engagement — ¿se quedan o rebotan?
- **Tiempo de interacción promedio** → distingue visitas reales de rebotes rápidos
- **Sesiones con interacción** → GA4 considera "con interacción" a las que duran más de 10 segundos o tienen 2+ páginas vistas

### Navegación — ¿qué funciona y qué no?
- **Páginas más vistas** → qué contenido atrae tráfico
- **Páginas de entrada** → por dónde llega la gente (¿solo la home?)
- **Tiempo promedio por página** → qué páginas se leen y cuáles se ignoran

---

## Primeras concluciones

- ** Interés en Contacto y Eventos: Se observa que la página de "Contacto" y el evento "Fit Fest" están entre los más visitados, lo que sugiere que el tráfico tiene una alta intención de conversión o participación.

- ** Tasa de Rebote (0,0%): En la captura dashboard-navegacion.png se ve un rebote del 0%, lo cual es excelente; indica que los usuarios que entran están navegando al menos una página adicional o interactuando con el contenido.

## Estructura del repositorio

```
analytics-dashboard/
├── README.md
├── implementacion/
│   ├── gtag-snippet.html     # Snippet listo para pegar en el <head>
│   └── eventos-custom.js     # Ejemplos de eventos personalizados con gtag
├── dashboard/
│   └── estructura.md         # Descripción de cada bloque del dashboard
└── capturas/
    ├── dashboard-resumen.png
    └── dashboard-navegacion.png
```

---

## Cómo replicar este proyecto

1. Crear una propiedad en [Google Analytics 4](https://analytics.google.com)
2. Copiar el snippet de `implementacion/gtag-snippet.html` en el `<head>` de tu HTML
3. Reemplazar `G-XXXXXXXXXX` con tu Measurement ID real
4. Hacer deploy en Firebase Hosting (`firebase deploy --only hosting`)
5. Verificar en GA4 → Informes → Tiempo real que lleguen eventos
6. Conectar GA4 a [Looker Studio](https://lookerstudio.google.com) como fuente de datos
7. Armar el dashboard con los bloques descritos en `dashboard/estructura.md`

---

## Decisiones de diseño

**¿Por qué GA4 y no Firebase Analytics directamente?**  
Firebase Analytics está pensado para apps móviles. Para un sitio web estático, GA4 con `gtag.js` da más control sobre los eventos y mejor integración con Looker Studio.

**¿Por qué Looker Studio y no un dashboard custom?**  
El cliente no tiene conocimientos técnicos. Looker Studio genera un link compartible, se actualiza automáticamente y no requiere mantenimiento una vez configurado.

**¿Por qué no BigQuery?**  
El plan gratuito de Firebase no incluye export a BigQuery. Para las necesidades actuales del cliente (tráfico, navegación, engagement), la conexión directa GA4 → Looker Studio es suficiente y mantiene todo el stack en costo cero.

---

## Dashboard

> Las capturas muestran la estructura del dashboard con datos anonimizados.

![Resumen general](capturas/dashboard-resumen.png)  
*Bloque 1: resumen de tráfico, sesiones y usuarios nuevos vs recurrentes*

![Navegación](capturas/dashboard-navegacion.png)  
*Bloque 2: páginas más vistas, tiempo promedio por página y engagement*

---

## Sobre este proyecto

Proyecto real implementado para un cliente del sector salud y bienestar. Los datos del dashboard son privados; las capturas muestran la estructura con valores anonimizados.

**Tecnologías:** Firebase · Google Analytics 4 · Looker Studio · HTML / CSS / JS  
**Tipo:** Proyecto freelance · Analítica web · Dashboard de cliente

---

[nvherreramartinez](https://github.com/nvherreramartinez)
